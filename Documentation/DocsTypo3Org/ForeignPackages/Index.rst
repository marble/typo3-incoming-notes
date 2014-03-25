
.. include:: ../../Includes.txt

==================================================
Foreign Packages
==================================================

Rendered: |today|

:ref:`Sitemap <sitemap>`



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




.. toctree: :
   :maxdepth: 5
   :glob:
   :titlesonly:

   *


:ref:`Sitemap <sitemap>`

