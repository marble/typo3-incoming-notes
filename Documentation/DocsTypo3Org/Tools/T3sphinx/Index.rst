
.. include:: ../../../Includes.txt

==================================================
Python Package 't3sphinx'
==================================================

.. contents::
   :local:


:ref:`Sitemap <sitemap>`


t3sphinx
========

*t3sphinx* is a Python package that adds TYPO3 specific functionality to the Sphinx documentation tools.


Installation
------------

Verify that the script language Python is installed on your computer::

  $ python --version
  Python 2.7.6

A Python version 2.6.x or 2.7.x will do. *t3sphinx* has not yet been tested with Python 3.x.
Clone the repository and run the installer::

  $ cd ~
  $ git clone git://git.typo3.org/Documentation/RestTools.git
  $ cd ~/RestTools/ExtendingSphinxForTYPO3
  $ python setup.py install

To find out where that package has been placed on you machine run::

  $ python -c "import t3sphinx; print t3sphinx.__file__"
  /usr/local/lib/python2.6/dist-packages/t3sphinx/__init__.pyc
  $

or use the interactive mode of Python::

  $ python
  Python 2.6.6 (r266:84292, Dec 26 2010, 22:31:48)
  [GCC 4.4.5] on linux2
  Type "help", "copyright", "credits" or "license" for more information.
  >>> import t3sphinx
  >>> t3sphinx.__file__
  '/usr/local/lib/python2.6/dist-packages/t3sphinx/__init__.pyc'
  >>> exit()
  $


Invocation
----------

The TYPO3 specific functionality that *t3sphinx* provides will only be
activated when the usual Sphinx configuration file :file:`conf.py` is being
used **and** when *conf.py* contains the *TYPO3 specific code block*
near the end.

Copy that codeblock from `t3sphinx.resources.typo3_codeblock_for_conf.py`__
and paste it at the end of the :file:`conf.py` configuration file.

__ https://git.typo3.org/Documentation/RestTools.git/tree/HEAD:/ExtendingSphinxForTYPO3/src/t3sphinx/resources

.. important::

   Make sure that the relative path from *conf.py* to *master_doc* is set correctly.
   In TYPO3 projects we usually use this structure::

       ./project/Documentation/Index.rst      (= master_doc)
       ./project/Documentation/_make/conf.py

   This is the reason why we have ``..`` as relative path in the TYPO3 specific
   code block. Adapt the following line if your :file:`conf.py`is placed somewhere
   else::

		# relative path from conf.py to master_doc
		t3DocTeam['relpath_to_master_doc'] = '..'

Developmental version of *t3sphinx*
-----------------------------------

A howto for developers:

  1. `Find out <Installation>`_ where your current *t3sphinx* resides

  2. Clone the `current developers version of t3sphinx`__ from Github

  3. Replace the folder ``... t3sphinx/``.

__ https://github.com/marble/typo3-resttools-t3sphinx

.. attention::

   Make sure to use the new `code-block-for-typo3`__

   __ https://github.com/marble/typo3-resttools-t3sphinx/blob/master/resources/typo3_codeblock_for_conf.py

The *codeblock for TYPO3* has now changed changed for the first time and carries
``version: 2014-03-23`` as an identifier. New are the settings *html_translator_class*
and *locale_dirs*.


:ref:`Sitemap <sitemap>`

