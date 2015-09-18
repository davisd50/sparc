*SPARC*
=====

Security Packages for Analysis and Rapid Coding

DEV BUILDOUT
------------
Buildout (www.buildout.org) is used to instantiate a development environment.
These are the steps to get you going.

 - *Enable PATH for the Python interpreter you'd like to work off.  The following
   assumes you've setup a sparc.python (see
   https://github.com/davisd50/sparc.python) environment [unix only].
   Otherwise, simply update your PATH with the correct python[.exe] you'd like
   use, or use full-path python calls below.*
   - cd [to directory where sparc.python was built]
   - source etc/profile

 - *Create a virtual Python environment to be used by the buildout*
   - cd [to a directory that have Python virtual environments]
   - virtualenv sparc --no-setuptools
   - source sparc/bin/activate [unix]
   - sparc\Scripts\activate.bat [windows]

 - *Checkout sparc from GITHUB [this only checks out a READ-only version of sparc]*

   [clone repository]
   - cd [to a directory that will host your dev projects]
   - git clone https://github.com/davisd50/sparc.git

 - Go into the GIT checkout location of sparc
   - cd [your filesystem checkout location of the sparc GIT project]

 - *Install some base required packages into the virtualenv.*

   [install required packages]
   - python ez_setup.py
   - easy_install setuptools==8.0
   - easy_install pip [not really needed, but avoids PATH confusion with system Python]

 - *Bootstrap the buildout*
   - python bootstrap.py

 - *Buildout the...err..buildout for development*
   - bin/buildout -c develop.cfg [unix]
   - bin\buildout -c develop.cfg [windows]
