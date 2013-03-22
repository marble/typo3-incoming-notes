.. ==================================================
.. FOR YOUR INFORMATION 
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.  ÄÖÜäöüß

.. include:: ../Includes.txt


=================================
Paths example
=================================


github.com/froemken/typo3-extbase-guide.git
===========================================

Compilation of relevant paths::

        https://github.com/froemken/typo3-extbase-guide.git
        
        http://docs.typo3.org/~mbless/github.com/froemken/typo3-extbase-guide.git.make/
        http://docs.typo3.org/~mbless/github.com/froemken/typo3-extbase-guide.git.make/request_rebuild.php
        
                  /home/mbless/HTDOCS/github.com/froemken/typo3-extbase-guide.git.make/
                  /home/mbless/HTDOCS/github.com/froemken/typo3-extbase-guide.git.make/conf.py
                  /home/mbless/HTDOCS/github.com/froemken/typo3-extbase-guide.git.make/cron_rebuild.sh
                  /home/mbless/HTDOCS/github.com/froemken/typo3-extbase-guide.git.make/Makefile
        
    http://docs.typo3.org/typo3cms/drafts/github/froemken/ExtbaseGuide/
 /home/mbless/public_html/typo3cms/drafts/github/froemken/ExtbaseGuide

This needs to go to conf.py::

    t3DocTeam['relpath_to_master_doc'] = '../typo3-extbase-guide.git/Documentation'
    

This needs to go to Makefile::

    BUILDDIR      = /home/mbless/public_html/typo3cms/drafts/github/froemken/ExtbaseGuide
    [...]
    ALLSPHINXOPTS   = -d $(BUILDDIR)/doctrees $(PAPEROPT_$(PAPER)) $(SPHINXOPTS) ../typo3-extbase-guide.git/Documentation
    [...]
    I18NSPHINXOPTS  = $(PAPEROPT_$(PAPER)) $(SPHINXOPTS) ../typo3-extbase-guide.git/Documentation


This needs to go to .../typo3-extbase-guide.git.make/cron_rebuild.sh::

    pushd /home/mbless/HTDOCS/github.com/froemken/typo3-extbase-guide.git.make/
    [...]
    cd /home/mbless/HTDOCS/github.com/froemken/typo3-extbase-guide.git/
    [...]
    cd /home/mbless/HTDOCS/github.com/froemken/typo3-extbase-guide.git.make/
    


Add to cron job processing::

    in:        /home/mbless/HTDOCS/git.typo3.org/Documentation/cron_rebuild.sh
    add line:  /home/mbless/HTDOCS/github.com/froemken/typo3-extbase-guide.git.make/cron_rebuild.sh


Make the manual known to hook processing::

    in:        /home/mbless/public_html/services/handle_github_post_receive_hook.php
    add line:  	'https://github.com/froemken/typo3-extbase-guide.git' => 'http://docs.typo3.org/~mbless/github.com/froemken/typo3-extbase-guide.git.make/request_rebuild.php',

