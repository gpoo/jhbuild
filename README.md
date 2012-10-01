Building Evince
===============

[Evince][1] is a document viewer (tipically for PDF/DVI/PS files among others).

Preparing the environment
-------------------------

In a Debian/Ubuntu machine, you have to install the dependencies to build
evince and install jhbuild.

    $ sudo apt-get build-dep evince
    $ sudo apt-get install jhbuild

You can also get the latest `jhbuild` from GNOME repositories in 
http://git.gnome.org/browse/jhbuild.  However, it should not be
necessary.

Building Evince and its dependencies
------------------------------------

Grab the configuration file for `jhbuild` and build the basic dependencies
for evince (poppler, a newer glib and evince itself):

    $ wget https://raw.github.com/gpoo/jhbuild/master/jhbuildrc-evince
    $ jhbuild -f jhbuildrc-evince build
    $ jhbuild -f jhbuildrc-evince run evince

The source code will be downloaded to your `$HOME/code/evince/checkout` and
install in `$HOME/code/evince/install`.

  [1]: http://projects.gnome.org/evince/

