e-cidadania
===========

Installing dependencies in OS Ubuntu 12.04 (32b)
Ubuntu 12.04 comes with python v 2.7.3 by default.
Furthermore, e-cidadania has been developed on python 2.7

[4FIRST]

(X) sudo apt-get update
(X) sudo apt-get upgrade

(X) sudo apt-get install build-essential python python-dev

(X) sudo apt-get install nginx nginx-full uwsgi uwsgi-plugin-python
(?) sudo apt-get install mysql-server mysql-client libmysqlclient-dev
(X) wget https://bitbucket.org/pypa/setuptools/raw/bootstrap/ez_setup.py -O - | python

[OR:: UWSGI.pip.IF]
(X) sudo pip install http://projects.unbit.it/downloads/uwsgi-lts.tar.gz
(*?*) sudo useradd -c 'uwsgi user' -g nginx --system \

(i) sudo netstat -tap | grep mysql (Data::Running...?:)
(i) sudo service mysql start|stop|restart


[OptionalDevs :: htop|aptitude]

(X) sudo apt-get install htop
(X) sudo apt-get install aptitude



Installation
------------

Since e-cidadania 0.1.5 we include an automated buildout system. 
If you want to install it to do testing or development you should see these instructions:
"<https://github.com/cidadania/e-cidadania/blob/gsoc2012/docs/en/dev/environment.rst>"

[Minimal Security]

(X) adduser -m <userName>
(X) adduser <userName> sudo
(X) visudo 
          # User privilege specification
            <userName> ALL=(ALL:ALL) ALL


  
[PreRequisites]

(?) sudo apt-get install pip
(?) sudo pip install MySQL-Python
(?) sudo pip install -U setuptools

(X) sudo apt-get install git-core
(X) sudo apt-get install supervisor
(X) sudo apt-get install python-setuptools

(X) sudo apt-get install python-imaging
(X) sudo apt-get build-dep python-imaging
(X) sudo apt-get install libjpeg62 libjpeg62-dev
(E) |i| You must put some 'source' URIs in your sources.list


[OPTional] Aptitude 
(X) sudo aptitude show python-imaging
(X) sudo aptitude install python-pythonmagick python-markdown python-textile python-docutils

[Esenciales]

(X) sudo apt-get install python-dev libjpeg-dev libfreetype6-dev zlib1g-dev
(X) sudo apt-get install build-essential libxml2-dev libxslt1-dev
(X) sudo apt-get install libcurl4-gnutls-dev libexpat1-dev gettext libz-dev libssl-dev


[(4FIRST2...Optional OR Not:)]
( ) sudo pip install virtualenv virtualenvwrapper
(X) git clone https://github.com/jjoc/e-cidadania (Ofc.Release?:)
(X) ln -s "/home/citizen/deploy/e-cidadania/src/e_cidadania/settings" config

[(CONFIGs.DROP5.org)(nginx.conf)]

(X) sudo wget ftp://drop5org@ftp.drop5.org/httpdocs/eCidadania/nginx_conf_prod_ecidadania
(X)  * cp nginx.drop5.org >>> /etc/nginx >>> nginx.conf |i| vim locations |i| maps, google, skype...




[INSTALLATION]
(X) sudo apt-get update
(X) sudo apt-get upgrade
(X) sudo pip install -r requirements.txt


[StartING Nginx]

(X) sudo nginx -t (Data::Running...?:)

__init__.py  debug = false
/etc/nginx UPLOAD nginx.conf (drop5.org)
(modifiK IP, rutas, etc.)



[StartING Supervisor]

(X) sudo apt-get install supervisor
(X) sudo touch ecidadania.conf 

(i)  "contenido" ecidadania.conf /etc/supervisor/conf.d/  (Data::Running...?:)

------------------------------------------------------------------------------
[program:ecidadania]
user=USUARIO
command=/usr/bin/uwsgi_python27 --socket=/tmp/ecidadania.sock
                       --chmod-socket=666
               (**)    --chdir=/directorio/de/codigo/fuente/src
                       --workers 5
               (**)    --single-interpreter --enable-threads
                       /directorio/a/archivo/wsgi.py
------------------------------------------------------------------------------

/etc/supervisor UPLOAD ecidadania.conf (drop5.org) (modifiK IP, rutas, etc.)



***********[ALTERNATIVE Synapse Connectot SETUP] Nginx, uWSGI, Python, Django Server [EXCLUYENTE]***********


[Install uWSGI]

(X) sudo apt-get install uwsgi uwsgi-plugin-python
(X) sudo useradd -c 'uwsgi user' -g nginx --system \
[i] --no-create-home --disabled-login --disabled-password uwsgi

[i] UPStart :: configuration file at /etc/init/uwsgi.conf ::

-----------------------------------------------------------------------------------*
1 description "uWSGI"
2 start on runlevel [2345]
3 stop on runlevel [06]
4 
5 respawn
6
7 exec uwsgi --master --processes 4 --die-on-term --uid uwsgi --gid nginx \
8 --socket /tmp/uwsgi.sock --chmod-socket 660 --vhost --logto /var/log/uwsgi.log \
9 --plugins python
-----------------------------------------------------------------------------------*



[Install Nginx(Latest Estable::AddKey]


(X) sudo wget http://nginx.org/keys/nginx_signing.key
(X) sudo apt-key add nginx_signing.key
(I) **open up the /etc/apt/sources.list file and append the following:

*----------------------------------------------------------*
*deb http://nginx.org/packages/ubuntu/ precise nginx
*deb-src http://nginx.org/packages/ubuntu/ precise nginx
*----------------------------------------------------------*

(X) sudo apt-get install nginx
(X) sudo nginx -t                           (Data::Running...?:)

******************************************[/ALTERNATIVA EXCLUYENTE]*******************************************






* Configure *src/e_cidadania/settings/production.py* to you desire.
* Set *src/e_cidadania/settings/__init__.py* DEBUG to False
* Generate the database with "SRC" ::


(* Make all the south migrations :: Copy all the static files)


(X) python manage.py syncdb      
(X) pytohn manage.py migrate
(X) python manage.py collectstatic


* Run the development server (???)

(?) python manage.py
(X) python manage.py runserver
(?) python manage.py runserver 1.2.3.4:8000 (where 1.2.3.4 is your IP Server)




-----------
Development
-----------

**We need developers! If you want to join us, send an email to info@ecidadania.org**

Development and bugtracking is done through `code.ecidadania.org <http://code.ecidadania.org>`_

 * `IRC channels <http://webchat.freenode.net>`_ #ecidadania-dev and #ecidadania for e-cidadania.

Useful information
------------------

 * `Design concepts <http://code.ecidadania.org/wiki/DesignConcepts>`_ design concepts, this are the guides to follow when developing.
 * `Releases <http://code.ecidadania.org/wiki/Releases>`_ version roadmap. This is where we stablish the features, release 
