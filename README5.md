![](http://ecidadania.org/uploads//spaces/logos/ecidadania.png)![](https://secure.gravatar.com/avatar/c3513d5274ea954547dedfeefd88df34?s=130)

    Synapse Constructors 4A e-Cidadania's OneClick Deployement

![](http://i.imgur.com/BeE14Bl.png)
![](http://i.imgur.com/5ldxDJl.png)
[![CI Build Status](https://secure.travis-ci.org/intridea/omniauth.png?branch=master)][travis]
[![Dependency Status](https://gemnasium.com/intridea/omniauth.png?travis)][gemnasium]
[![Coverage Status](https://coveralls.io/repos/intridea/omniauth/badge.png?branch=master)][coveralls]
[![Bitdeli Badge](https://d2weczhvl823v0.cloudfront.net/intridea/omniauth/trend.png)](https://bitdeli.com/free "Bitdeli Badge")

[gem]: https://rubygems.org/gems/omniauth
[travis]: http://travis-ci.org/intridea/omniauth
[gemnasium]: https://gemnasium.com/intridea/omniauth
[coveralls]: https://coveralls.io/r/intridea/omniauth


![](http://doc.ubuntu-es.org/images/a/ae/Oil-logo-ubuntu.png)**Installing dependencies in OS Ubuntu 12.04 (32b)**


    *(X) apt-get update
    *(X) apt-get upgrade
    *(X) wget https://bitbucket.org/pypa/setuptools/raw/bootstrap/ez_setup.py -O - | python

![](https://github-camo.global.ssl.fastly.net/c1cd2f9c78f091da772eebf11e3f53946c211442/687474703a2f2f69636f6e732e69636f6e617263686976652e636f6d2f69636f6e732f6d696c6f737a2d776c617a6c6f2f626f6f6d792f33322f757365722d6c6f636b2d69636f6e2e706e67) **[User Security]**

    (X) adduser <userName>
    (X) adduser <userName> sudo
    (X) visudo 
      # User privilege specification
        <userName> ALL=(ALL:ALL) ALL


![](http://wiki.team-mediaportal.com/@api/deki/files/1523/=alert_icon.png) **[PreRequisites]**


    (X) sudo apt-get install git-core
    (X) sudo apt-get install supervisor
    (X) sudo apt-get install python-setuptools python-pip
    (X) sudo apt-get install nginx nginx-full uwsgi uwsgi-plugin-python
    (X) sudo apt-get install mysql-server mysql-client libmysqlclient-dev
    (X) sudo apt-get install python-dev libjpeg-dev libfreetype6-dev zlib1g-dev
    (X) sudo apt-get install build-essential python-dev libxml2-dev libxslt1-dev
    (X) sudo apt-get install libcurl4-gnutls-dev libexpat1-dev gettext libz-dev libssl-dev

![](http://iconza.com/download/164/32x32/2a15d9/workflow.png) **[OptionalDevs]**

    (?) sudo apt-get install aptitude
    (?) sudo apt-get install htop

**[Optional Enviroment & GetSource]**

    ( ) sudo pip install virtualenv
    (X) git clone https://github.com/jjoc/e-cidadania
    (X) ln -s "/home/citizen/deploy/e-cidadania/src/e_cidadania/settings" config


**[MySQL Install & Status]**

    (X) sudo apt-get install python-mysqldb mysql-python
    (i) sudo netstat -tap | grep mysql (Data::Running...?:)
    (i) sudo service mysql start|stop|restart
    
**[Others Comprobations]**


    (i) sudo service uwsgi restart (Data::Running...?:)
    (i) sudo service nginx restart (Data::Running...?:)
    
**[IF "errors" NGINX]**


    (X) sudo fuser -k 80/tcp 
    (X) sudo /etc/init.d/nginx restart



**[OptionalDevs :: htop|aptitude]**

    (X) sudo apt-get install htop
    (X) sudo apt-get install aptitude



**[OPTional Aptitude]**

    (X) sudo aptitude show python-imaging
    (X) sudo aptitude install python-pythonmagick python-markdown python-textile python-docutils

**[Esenciales | Essentials]**

    (X) sudo apt-get install python-dev libjpeg-dev libfreetype6-dev zlib1g-dev
    (X) sudo apt-get install build-essential libxml2-dev libxslt1-dev libpq-dev libssl-dev
    (X) sudo apt-get install libcurl4-gnutls-dev libexpat1-dev gettext libz-dev libxslt-dev




**[INSTALLATION]**

    (X) sudo apt-get update
    (X) sudo apt-get upgrade
    (X) sudo pip install -r requirements.txt

**[CONFIGURATION & STARTup's]**

*[StartING Nginx]*

    __init__.py  debug = false
    /etc/nginx UPLOAD nginx.conf (drop5.org)
    (modifiK IP, rutas, etc.)

*[StartING Supervisor]*

    /etc/supervisor UPLOAD ecidadania.conf (drop5.org)
    (modifiK IP, rutas, etc.)


    































**We need developers! If you want to join us, send an email to info@ecidadania.org**

Development and bugtracking is done through `code.ecidadania.org <http://code.ecidadania.org>`_

Getting help
------------

 * `Documentation <http://code.ecidadania.org/wiki/Documentation>`_ e-cidadania documentation.
 * `Mailing lists <http://code.ecidadania.org/wiki/MailingLists>`_ global and local.
 * `Social networks <http://code.ecidadania.org/wiki/SocialNetworks>`_ where e-cidadania present.
 * `Website <http://ecidadania.org>`_ e-cidadania official website.
 * `IRC channels <http://webchat.freenode.net>`_ #ecidadania-dev and #ecidadania for e-cidadania.

Useful information
------------------

 * `Design concepts <http://code.ecidadania.org/wiki/DesignConcepts>`_ design concepts, this are the guides to follow when developing.
 * `Releases <http://code.ecidadania.org/wiki/Releases>`_ version roadmap. This is where we stablish the features, release dates and other things of every version.

Collaborate
-----------

* **Developing** You can take the last code from the repository and experiment with it. When you're done, you can send us a "Merge request". Please check the `How To Contribute <http://code.ecidadania.org/wiki/HowToContribute>`_ page.

* **Documenting** Right now the documentation is a bit insufficient. If you want to document e-cidadania, feel free to do it. We use Sphinx (1.1.3) to generate the documents.

* **Translating**  You can contribute translating e-cidadania from its page on `Transifex <http://www.transifex.net/projects/p/ecidadania/>`_. If you need a language that is not available, ask for it from Transifex and we will create it ASAP.

* **Bug reporting** You can report the bugs you find in the application in this trac: http://code.ecidadania.org


