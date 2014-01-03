e-cidadania
===========

.. image:: https://badge.fury.io/gh/cidadania%2Fe-cidadania.png
    :target: http://badge.fury.io/gh/cidadania%2Fe-cidadania
.. image:: http://i.imgur.com/BeE14Bl.png
    :target: http://python.org
.. image:: http://i.imgur.com/5ldxDJl.png
    :target: http://djangoproject.com

e-cidadania is a project to develop an open source application for citizen
participation, which can be used for debates, proposals, trusted voting,
usable by associations, companies and administrations.

The e-cidadania objective is to provide a way to make a full participation
process on internet, or even use it as a complement to in person participative
processes.

Installation
------------

Since e-cidadania 0.1.5 we include an automated buildout system. If you want to
install it to do testing or development you should see
`these instructions <https://github.com/cidadania/e-cidadania/blob/gsoc2012/docs/en/dev/environment.rst>`_

If you don't want to create an isolated development environment:

* Download the source code from git, or from the official webpage.
* You need to install the python packages specified in requirements.txt for
  e-cidadania, you can do it with pip::
  
(X) sudo apt-get install git-core
(X) sudo apt-get update
(X) sudo apt-get install libcurl4-gnutls-dev libexpat1-dev gettext libz-dev libssl-dev build-essential
(X) sudo apt-get install python-setuptools
(X) sudo easy_install pip

[Optional]
( ) sudo pip install virtualenv
(X) git clone https://github.com/jjoc/e-cidadania


[INSTALLATION]
(X) sudo apt-get update
(X) sudo apt-get upgrade
(X) sudo pip install -r requirements.txt

* Configure *src/e_cidadania/settings/production.py* to you desire.
* Set *src/e_cidadania/settings/__init__.py* DEBUG to False
* Generate the database with::

    python manage.py syncdb

* Make all the south migrations::

    pytohn manage.py migrate

* Copy all the static files::

    python manage.py collectstatic

* Run the development server

    python manage.py runserver

**e-cidadania currently supports python 2.7.X. The work for porting to python 3 is on the "python3" branch.**

Demonstration
-------------

There is a demo running in the website http://demo.ecidadania.org.

Development
-----------

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
