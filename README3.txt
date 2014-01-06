e-cidadania
===========

Installing dependencies in OS Ubuntu 12.04 (32b)
Ubuntu 12.04 comes with python v 2.7.3 by default.
Furthermore, e-cidadania has been developed on python 2.7

Installation
===============


[4FIRST RequeriMents]

(X) apt-get update
(X) apt-get upgrade

(X) apt-get install build-essential python python-dev

(X) apt-get install nginx nginx-full uwsgi uwsgi-plugin-python
(?) apt-get install mysql-server mysql-client libmysqlclient-dev
(X) wget https://bitbucket.org/pypa/setuptools/raw/bootstrap/ez_setup.py -O - | python


[Optional Security]

(X) adduser <userName>
(X) adduser <userName> sudo
(X) visudo 
          # User privilege specification
            <userName> ALL=(ALL:ALL) ALL
            
           

[PreRequisites]

(?) sudo easy_install pip
(?) sudo pip install MySQL-Python
(?) sudo pip install -U setuptools

(X) sudo apt-get install git-core
(X) sudo apt-get install supervisor
(X) sudo apt-get install python-setuptools

(X) sudo apt-get install python-imaging
(X) sudo apt-get build-dep python-imaging
(X) sudo apt-get install libjpeg62 libjpeg62-dev
(E) |i| You must put some 'source' URIs in your sources.list


[OR:: UWSGI.pip.IF]

(X) sudo pip install http://projects.unbit.it/downloads/uwsgi-lts.tar.gz

*** uWSGI is ready, launch it with /usr/local/bin/uwsgi ***
(*?*) sudo useradd -c 'uwsgi user' -g nginx --system \
>     --no-create-home --disabled-login --disabled-password uwsgi

************************************************************************
***** citizen@ipirates:~$ sudo useradd -c 'citizen' -g nginx --system \
***** > --no-create-home --disabled-login --disabled-password uwsgi
***** useradd: group 'nginx' does not exist
*************************************************************************



[MySQL Status]

(i) sudo netstat -tap | grep mysql (Data::Running...?:)
(i) sudo service mysql start|stop|restart


[OptionalDevs :: htop|aptitude]

(X) sudo apt-get install htop
(X) sudo apt-get install aptitude



[OPTional] Aptitude 
(X) sudo aptitude show python-imaging
(X) sudo aptitude install python-pythonmagick python-markdown python-textile python-docutils

[Esenciales]

(X) sudo apt-get install python-dev libjpeg-dev libfreetype6-dev zlib1g-dev
(X) sudo apt-get install build-essential libxml2-dev libxslt1-dev libpq-dev libssl-dev
(X) sudo apt-get install libcurl4-gnutls-dev libexpat1-dev gettext libz-dev libxslt-dev


[(4FIRST2...Optional OR Not:)]
( ) sudo pip install virtualenv virtualenvwrapper
(X) git clone https://github.com/jjoc/e-cidadania (Ofc.Release?:)
(X) ln -s "/home/citizen/e-cidadania/src/e_cidadania/settings" config

[(CONFIGs.DROP5.org)(nginx.conf)]

(X) sudo wget ftp://drop5org@ftp.drop5.org/httpdocs/eCidadania/nginx_conf_prod_ecidadania
(X)  * cp nginx.drop5.org >>> /etc/nginx >>> nginx.conf |i| vim locations |i| maps, google, skype...

____________________________________________________________________________________________________

user root root;

worker_processes  10;

error_log /var/log/nginx/error_log info;

events {
    worker_connections 1024;
    use epoll;
    accept_mutex on;
}

http {
    include                     /etc/nginx/mime.types;
    default_type                application/octet-stream;

    log_format main
        '$remote_addr - $remote_user [$time_local] '
            '"$request" $status $bytes_sent '
        '"$http_referer" "$http_user_agent" '
        '"$gzip_ratio"';

    client_header_timeout       10m;
    client_body_timeout         10m;
    client_max_body_size        200M;
    send_timeout                10m;
    connection_pool_size        256;
    client_header_buffer_size   1k;
    large_client_header_buffers 4 2k;
    request_pool_size           4k;

    gzip                        on;
    gzip_min_length             1024;
    gzip_buffers                32 4k;
    gzip_types  text/plain application/x-javascript image/gif text/javascript
    text/css application/javascript application/xml image/png image/jpg
    application/xml+rss image/jpeg;

    output_buffers              1 32k;
    postpone_output             1460;
    sendfile                    on;
    tcp_nopush                  on;
    tcp_nodelay                 on;
    keepalive_timeout           75 20;
    ignore_invalid_headers      on;
    index                       index.html;

    server {
        listen 80 backlog=512;
        server_name 93.188.161.10;
        client_max_body_size 200M;
}

        location /humans.txt {
            alias /home/citizen/e-cidadania/src/e_cidadania/static_files/humans.txt;
        }


        location /uploads  {
            alias /home/citizen/e-cidadania/src/e_cidadania/uploads;
            location ~* ^.+\.(jpg|jpeg|gif|png|ico|css|zip|tgz|gz|rar|bz2|doc|xls|exe|pdf|ppt|txt|tar|mid|midi|wav|bmp|rtf|js|mov) {
                access_log   off;
                expires      1d;
                client_max_body_size 200m;
            }
        }






        location /static  {
            alias /directorio/>>>>>>>>>>>>>>>>estaticos;
            location ~* ^.+\.(jpg|jpeg|gif|png|ico|css|zip|tgz|gz|rar|bz2|doc|xls|exe|pdf|ppt|txt|tar|mid|midi|wav|bmp|rtf|js|mov) {
                access_log   off;
                expires      1d;
            }
        }

        location / {
            uwsgi_pass unix:/tmp/ecidadania.sock;
            include uwsgi_params;
            client_max_body_size 200M;
        }

        access_log  /var/log/nginx/ecidadania.org.access_log main;
        error_log   /var/log/nginx/ecidadania.org.error_log;
    }
}
     

_________________________________________________________________________________________________________


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
user=citizen
command=/usr/bin/uwsgi_python27 --socket=/tmp/ecidadania.sock
                       --chmod-socket=666
                       --chdir=/home/citizen/e-cidadania/src
                       --workers 5
                       --single-interpreter --enable-threads
                       /home/citizen/e-cidadania/src/wsgi.py

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

[NGINX CONFIG] <APP>





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


[HISTORYs]*********************************

ROOT:
    1  apt-get update
    2  apt-get upgrade
    3  sudo apt-get install git-core
    4  sudo apt-get update
    5  sudo apt-get install nginx
    6  sudo apt-get install build-essential python-dev
    7  sudo apt-get install libxslt1-dev
    8  sudo apt-get update python-dev libjpeg-dev libfreetype6-dev zlib1g-dev
    9  sudo apt-get install python-dev libjpeg-dev libfreetype6-dev zlib1g-dev
   10  sudo apt-get install libcurl4-gnutls-dev libexpat1-dev gettext libz-dev libssl-dev build-essential
   11  sudo apt-get install python-setuptools
   12  sudo easy_install pip
   13  sudo pip install uwsgi
   14  sudo apt-get install python-setuptools
   15  pip install -U setuptools
   16  Wheel installs require setuptools >= 0.8 for dist-info support.
   17  pip's wheel support requires setuptools >= 0.8 for dist-info support.
   18  Storing debug log for failure in /root/.pip/pip.log
   19  sudo pip install -U setuptools
   20  wget https://bitbucket.org/pypa/setuptools/raw/bootstrap/ez_setup.py -O - | python
   21  sudo pip install uwsgi

CITIZEN:

 
  192  cd etc/supervisor
 
  194  sudo vim ecidadania.conf

  205  sudo pip install -r requirements.txt

  213  sudo vim /etc/supervisor/conf.d/ecidadania.conf

  216  sudo vim /etc/supervisor/conf.d/ecidadania.conf
 
  219  cd supervisor

  221  sudo vim ecidadania.conf
  
  225  sudo vim nginx.conf
  226  sudo service nginx reload
  227  sudo supervisorctl
  228  sudo service supervisor start

  232  htop
  233  sudo service mysql status
 
  240  nginx -V | grep --color -o http_stub_status
  241  vi nginx.conf
  242  sudo service --status-all
  243  sudo service mysql status
  244  python manage.py

  255  python manage.py
  256  python manage.py syncdb
  257  pytohn manage.py migrate
  258  python manage.py migrate
  259  python manage.py collectstatic
  260  python manage.py runserver
 


  266  vim production.py
 
 
  289  sudo apt-get install nginx nginx-full uwsgi uwsgi-plugin-python
 
  297  supervisorctl
  298  sudo service supervisor start
  299  sudo service nginx status
  300  sudo service mysql status
  301  sudo service --status-all

 
  324  vim setup.py
  342  vim urls.py
 
  378  find -name django
  379  sudo find -name django
  380  cd /usr/local/lib/python2.7/dist-packages/django

  384  vim base.py

  397  sudo vim __init__.py

  401  sudo visudo


[/HISTORYs]




-----------
Development
-----------

**We need developers! info@ecidadania.org ** http://code.ecidadania.org 
**IRC channels <http://webchat.freenode.net>`_ #ecidadania-dev and #ecidadania for e-cidadania.

Useful information
------------------

 * `Design concepts <http://code.ecidadania.org/wiki/DesignConcepts>`_ design concepts, this are the guides to follow when developing.
 * `Releases <http://code.ecidadania.org/wiki/Releases>`_ version roadmap. This is where we stablish the features, release 
