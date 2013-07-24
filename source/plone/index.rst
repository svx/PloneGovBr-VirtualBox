======
Plone
======

.. contents:: :local:

Requirements
-------------

Packages you need to run Plone::

    python-setuptools python-dev build-essential libssl-dev libxml2-dev
    libxslt1-dev libbz2-dev

Optional packages::

    libjpeg62-dev libreadline-gplv2-dev wv poppler-utils python-imaging

It is always handy to install also::

    subversion git

For this Image we used the `install.plone.dependencies`_ script to install all
needed dependencies.

.. _install.plone.dependencies: https://github.com/collective/install.plone.dependencies

Install
-------

Make sure to be in */home/plonegovbr* !

Checkout buildout from Github::

    git clone git@github.com:plonegovbr/portal.buildout.git PloneGovBr

Create virtualenv, to use its own Python::

    virtualenv --python=python2.7 --no-site-packages PloneGovBr

Create the folder *downloads*::

    mkdir downloads

Create buildout.cfg::

    [buildout]
    extends = staging.cfg

Bootstrap::

    python bootstrap.py

Run buildout::

    ./bin/buildout -vvvv
