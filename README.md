sparc
=====

Security Packages for Analysis and Rapid Coding

DEV BUILDOUT
=====
Getting buildout to work inside the GE network can be...hmm..tedious.  To help
this process, you can use the scripts/buildout[.cmd] scripts (unix/windows).
If you want to do it manually, follow the process below.

 - Enable PATH for the Python interpreter you'd like to work off.  The following
   assumes you've setup a sparc.python (see
   https://github.build.ge.com/210071421/sparc.python) environment [unix only].
   Otherwise, simply update your PATH with the correct python[.exe] you'd like
   use, or use full-path python calls bbelow.
   # cd [to directory where sparc.python was built]
   # source etc/profile

 - Create a virtual Python environment to be used by the buildout
   # cd [to a directory that have Python virtual environments]
   # virtualenv sparc --no-setuptools
   # source sparc/bin/activate [unix]
   # sparc\Scripts\activate.bat [windows]

 - Checkout sparc from GITHUB [this only checks out a READ-only version of sparc]

   [set GIT variable to ignore cert errors]
   # export GIT_SSL_NO_VERIFY=true [unix]
   # set GIT_SSL_NO_VERIFY=true [windows]
   
   [clone repository]
   # cd [to a directory that will host your dev projects]
   # git clone https://github.build.ge.com/210071421/sparc.git sparc

 - Go into the GIT checkout location of sparc
   # cd [your filesystem checkout location of the sparc GIT project]

 - Install some base required packages into the virtualenv.  Inside the GE network,
   this will require access to the Internet via a Proxy.  I've listed one
   possible method to enable Python-based Internet access via a GE proxy
   without authentication

   [setup proxy]
   # source scripts/ge-proxy-on [unix]
   # scripts/ge-proxy-on.bat [windows]

   [install required packages]
   # python ez_setup.py
   # easy_install setuptools==8.0
   # easy_install pip [not really needed, but avoids PATH confusion with system Python]

   [install packages that just won't work with our internal PyPi server + buildout]
   # easy_install PasteScript==1.7.5

 - Bootstrap the buildout
   # python bootstrap.py

   [disable proxy]
   # source scripts/ge-proxy-off [unix]
   # scripts/ge-proxy-off.bat [windows]

 - Buildout the...err..buildout for development
   # bin/buildout -c develop.cfg [unix]
   # bin\buildout -c develop.cfg [windows]
