This is a demonstration of how to install TurboGears 1.0 projects with
pip and virtualenv, using no network access for any dependences, which
are all included in local fully-pinned source distributions. 

It expects to be dropped into an existing TG project, and then you can
run `bootstrap.py` to install the project.  You might need to add
additional dependencies for your project in `requirements/`.

Features
--------

* No downloading anything, ever.
* Setuptools 0.6c8 is guaranteed to be installed; this is necessary
  for the version of TG my projects are developed against, because of
  a change in the behavior of pkg_resources.resource_filename in
  setuptools 0.6c9 and greater.
* Two-phase installation process -- some TG plugins can only be
  installed after TG itself is installed, because they use setuptools
  extensions provided by TG.  So the bootstrap script installs TG (and
  its dependencies) first, and then installs the things that need TG
  installed before they can be installed.
* Non-zero exit codes if the bootstrap script fails anywhere.
* Python 2.5 is required (specifically -- no 2.4- or 2.6+).

