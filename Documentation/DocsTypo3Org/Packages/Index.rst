
.. include:: ../../Includes.txt

==================================================
Packages
==================================================

Rendered: |today|

**Jump up and down on this page:**

.. contents::
   :local:


Debian
======

- python python-docutils python-sphinx python-pygments

- openoffice.org openoffice.org-core  # we want: Openoffice headless

- beanstalkd

- tidy

- fdupes # used by cron_rebuild.sh to hard-link identical files in /home/mbless/public_html/

- texlive-base texlive-latex-recommended texlive-latex-extra texlive-fonts-recommended make

..

  # root       sudo -H -u mbless /usr/bin/soffice -headless -nologo -nofirststartwizard -accept=socket,host=127.0.0.1,port=8100;urp
  # mbless     /bin/sh /usr/bin/soffice -headless -nologo -nofirststartwizard -accept=socket,host=127.0.0.1,port=8100;urp
  # mbless     /usr/lib/openoffice/program/soffice.bin -headless -nologo -nofirststartwizard -accept=socket,host=127.0.0.1,port=8100;urp
  # 111        /usr/bin/beanstalkd -l 0.0.0.0 -p 11300


Python Packages
===============

setuptools
----------

Can be installed as Debian package "python-setuptools". The recommended installation method
for all systems is this: Download `ez_setup.py`__ and run ``python ez_setup.py``.

__ https://bitbucket.org/pypa/setuptools/raw/bootstrap/ez_setup.py

The *setuptools* function as a packet manager for Python packages that can resolve dependencies.
Once they are installed you can do a ``easy_install sphinx`` for example and all necessary packets
will be installed.


pyyaml
------

Early Python distributions don't come with Yaml modules. Install them: ``easy_install pyyaml``.


pygments
--------

Pygments_is a Python packet that provides syntax highlighting. It is used by Sphinx_.
If missing use the Debian package ``python-pygments``
or run ``easy_install pygments``.

.. _Pygments: http://pygments.org/
.. _Sphinx: http://sphinx-doc.org/

TypoScript Highlighting for Pygments
------------------------------------

1. Get the file `typoscript.py`__ from the RestTools__.

   __ https://git.typo3.org/Documentation/RestTools.git/blob/HEAD:/ExtendingPygmentsForTYPO3/_incoming/typoscript.py
   __ https://git.typo3.org/Documentation/RestTools.git

2. Find out where Pygments is installed on you system::

     $ python -c "import pygments; print pygments.__file__"

3. Copy :file:`typoscript.py`to the :file:`... /pygments/lexers/` folder

4. To register the new lexer go to the ``lexers/``folder and run ``(sudo) python _mapping.py``.



PHP
===

t3xutils.phar
-------------

https://github.com/etobi/Typo3ExtensionUtils
