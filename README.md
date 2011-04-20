This is a demonstration of how to install TurboGears 1.0.4 projects with
pip and virtualenv, using no network access for any dependences, which
are all included in local fully-pinned source distributions. 

You can clone this repo and run `bootstrap.py` to create a virtualenv
in `./ve` which can be used to run your TurboGears 1.0.4 project.
(Like `./ve/bin/python /path/to/my/project/start-myproject.py` for
example.) You might need to add additional dependencies for your
project in `requirements/` -- this contains all the core requirements
for a TurboGears 1.0.4 project.  (It also contains a few extra
requirements, so you may also want to prune some out, but it's
probably not really worth the bother.)

You can also use it to create new TurboGears 1.0.4 projects if you're
into that, e.g.:

    ./bootstrap.py
    ./ve/bin/tg-admin quickstart newproject
    ./newproject/start-newproject.py  # will have its shebang set to ../ve/bin/python

And then you can distribute the bootstrapper along with your project
so that it can be reliably rebuilt on other machines.

Features
--------

* Full containment in a virtualenv.
* Uses virtualenv 1.7-dev, pip 1.0
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

