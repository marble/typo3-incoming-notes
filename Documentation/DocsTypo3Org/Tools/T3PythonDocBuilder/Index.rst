
.. include:: ../../../Includes.txt

==================================================
T3PythonDocBuilder
==================================================

Rendered: |today|

**Jump up and down on this page:**

.. contents::
   :local:

What does it do?
================

It takes an OpenOffice document and does all necessary conversion and
transformation steps to produce a TYPO3 sphinx documentation project.

.. highlight:: bash

Copy this `./bin folder`__ from RestTools.git__ and run::

  $ python t3pdb_sxw2html.py --help

__ https://git.typo3.org/Documentation/RestTools.git/tree/HEAD:/T3PythonDocBuilderPackage/src/T3PythonDocBuilder
__ https://git.typo3.org/Documentation/RestTools.git

Openoffice
==========
It is expected that OpenOffice headless is up and running on the server.
We are using OpenOffice for converting OpenOffice documents to HTML.

.. attention::

   OpenOffice tends to "hang" if asked to convert SXW-manuals that aren't
   error free ZIP archives. Check for archive integrity before passing
   a conversion job over to OpenOffice.
