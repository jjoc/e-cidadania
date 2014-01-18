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
    
    

**[Esenciales | Essentials]**

    (X) sudo apt-get install python-dev libjpeg-dev libfreetype6-dev zlib1g-dev
    (X) sudo apt-get install build-essential libxml2-dev libxslt1-dev libpq-dev libssl-dev
    (X) sudo apt-get install libcurl4-gnutls-dev libexpat1-dev gettext libz-dev libxslt-dev



![](http://iconza.com/download/164/32x32/2a15d9/workflow.png) **[OptionalDevs]**

    (?) sudo apt-get install aptitude
    (?) sudo apt-get install htop

**[Optional Enviroment & GetSource]**

    ( ) sudo pip install virtualenv
    (X) git clone https://github.com/jjoc/e-cidadania
    (X) ln -s "/home/citizen/e-cidadania/src/e_cidadania/settings" configTeaTime (or koffe;)


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



**[INSTALLATION]**

    (X) sudo apt-get update
    (X) sudo apt-get upgrade
    (X) sudo pip install -r requirements.txt
    
**[FIRSs DEPLOYEMENTs]**

    (?) sudo python manage.py
    (?) sudo python *db/sinc/dump*
    (?) sudo pythonn *OTHERS DEPLOYs*


**[CONFIGURATION & STARTup's]**

*[StartING Nginx]*

    __init__.py  debug = false
    /etc/nginx UPLOAD nginx.conf (drop5.org)
    (modifiK IP, rutas, etc.)

*[StartING Supervisor]*

    /etc/supervisor UPLOAD ecidadania.conf (drop5.org)
    (modifiK IP, rutas, etc.)



![](http://www.citizenship.es/eDNIwww/img/DROP5eDNIwww55GitHub.png)eDNI.Voto.Click!
------------

**[Recomendados]**

    (X) sudo apt-get install dnie-tool libacr38u libccid libnss3-tools
    (X) sudo apt-get --purge remove dh-autoreconf             (*as build-dependency)
    
**[Pre-Requirements Java]**

    (X)
    (X)
    (X)
    
**[Pre-Requirements PHP]**

    (X) sudo apt-get install php5
    (X) sudo apt-get install libapache2-mod-php5
    (X)
    (X)
    (X)

**[PreRequisitos Entorno C]**

    (X) sudo apt-get install glade
    (X) sudo apt-get install libssl-dev
    (X) sudo apt-get install openssl g++
    (X) sudo apt-get install libssl0.9.8
    (X) sudo wget  xampp-linux-X.X.X.tar.gz
    (X) sudo tar xvfz xampp-linux-X.X.X.tar.gz –C /opt 
    (X) sudo apt-get install libccid libpcsclite1 pcscd pinentry-gtk2 pcsc-tools 
    (X) sudo apt-get install pcscd libccid libpcsclite-dev libssl-dev libreadline-dev 
    (X) sudo apt-get install autoconf automake build-essential docbook-xsl xsltproc libtool
    (X) sudo apt-get install build-essential pkg-config autoconf automake docbook-xsl subversion pcscd libpcsclite-dev pcsc-tools libreadline6 libreadline-dev libopenct-dev openssl libssl-dev libtool libltdl-dev libccid libassuan0 libassuan-dev pinentry-gtk2 

    
*[Download C+JavaPHP Source]*

    (X) sudo apt-get install unzip
    (X) sudo wget http://www.citizenship.es/eDNIwww/cSource/c_vot_cod13.zip -C /"c++DirSource"
    (X) sudo unzip c_vot_cod13.zip -d /"c++DirEXE"
    
*[StartING + www]*

    (X) sudo /opt/lampp/lampp start 
    (X) ./ guiVoto + servidorVoto + guiAdmin
    
    
-----------------------------------------------------------
#### How to build and install this eDNI-OSC package #######
-----------------------------------------------------------

**Prepare your system for build packages:**

    (X) sudo apt-get update
    (X) sudo apt-get install devscripts dpkg-dev fakeroot svn-buildpackage
    (X) sudo apt-get build-dep opensc

1. Get into your favorite release directory:
    
    (X) cd tags/xx.xx.xx/

or, if you want the bleeding edge:
cd trunk/

2. Check and install new build dependences if they exist:
    (X) sudo dpkg-checkbuilddeps
    (X) sudo apt-get install (*...*)

3. Get the current tarball for that release:
    (X) svn-buildpackage -rfakeroot -us -uc -tc --svn-download-orig

* If you use pbuild, do:
    (X) svn-buildpackage --svn-builder="pdebuild --use-pdebuild-internal --buildresult `pwd`/../build-area"     
    (X) --svn-download-orig

4. Install it:
    (X) sudo dpkg -i ../build-area/libopensc_*.deb ../build-area/opensc_*.deb 

5. Install all unmet dependences:
    (X) sudo apt-get -f install

6. Consider to configure your application (internet browser, etc) to support OpenSC
and install on it the needed certificates, if any.

7. Enjoy! ;)
    
    



.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.



    






























![](http://www.citizenship.es/eDNIwww/img/GreenButtonDeveloper55.png) **We need developers! If you want to join us, send an email to info@ecidadania.org**

Development and bugtracking is done through `code.ecidadania.org http://code.ecidadania.org
![](http://aulavirtual.uv.es/global/HELP/images/help.png)Getting help
------------

 * `Documentation http://code.ecidadania.org/wiki/Documentation _ e-cidadania documentation.
 * `Mailing lists http://code.ecidadania.org/wiki/MailingLists _ global and local.
 * `Social networks http://code.ecidadania.org/wiki/SocialNetworks _ where e-cidadania present.
 * `Website http://ecidadania.org _ e-cidadania official website.
 * `IRC channels http://webchat.freenode.net _ #ecidadania-dev and #ecidadania for e-cidadania.
 
![](http://upload.wikimedia.org/wikipedia/commons/thumb/f/f3/Logo_wikipedia_birrete.png/120px-Logo_wikipedia_birrete.png) Useful information
------------------

 * `Design concepts http://code.ecidadania.org/wiki/DesignConcepts _ design concepts, this are the guides to follow when developing.
 * `Releases http://code.ecidadania.org/wiki/Releases _ version roadmap. This is where we stablish the features, release dates and other things of every version.
 
![](http://kclocalmarketing.com/wp-content/uploads/2010/12/Collaborate.png) Collaborate
-----------

* **Developing** You can take the last code from the repository and experiment with it. When you're done, you can send us a "Merge request". Please check the `How To Contribute http://code.ecidadania.org/wiki/HowToContribute _ page.

* **Documenting** Right now the documentation is a bit insufficient. If you want to document e-cidadania, feel free to do it. We use Sphinx (1.1.3) to generate the documents.

* **Translating**  You can contribute translating e-cidadania from its page on `Transifex http://www.transifex.net/projects/p/ecidadania/ _. If you need a language that is not available, ask for it from Transifex and we will create it ASAP.

* **Bug reporting** You can report the bugs you find in the application in this trac: http://code.ecidadania.org


