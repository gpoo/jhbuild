Building Evince
===============

[Evince][1] is a document viewer (tipically for PDF/DVI/PS files among others).

Preparing the environment
-------------------------

### Debian and Ubuntu

In a Debian/Ubuntu machine, you have to install the dependencies to build
evince and install jhbuild.

The following steps have been tested to work well in Debian Wheezy and
Jessie (Testing), and Ubuntu 12.04 (Precise) and 13.04 (Rarian) after a
clean install.

To install the basic dependencies:

    $ sudo apt-get build-dep evince gobject-introspection at-spi2-core
    $ sudo apt-get install jhbuild curl yelp-tools gperf ragel cmake libgcrypt11-dev libcroco3-dev  icon-naming-utils valac

You can also get the latest `jhbuild` from [GNOME repositories][2] in.
However, it should not be necessary.

Then, prepare to build Evince in `~/jhbuild`:

    $ mkdir ~/jhbuild; cd ~/jhbuild
    $ curl -o jhbuildrc-evince https://people.gnome.org/~gpoo/build/evince/jhbuildrc-evince

### Fedora 19

The following steps have been tested to work well in Fedora 19 after a clean install.

To install the basic dependencies:

    $ sudo yum-builddep evince gobject-introspection at-spi2-core
    $ sudo yum install expat-devel gperf gcc-c++ ragel cmake libgcrypt-devel icon-naming-utils libcroco-devel vala

Then, prepare to build Evince in `~/jhbuild`:

    $ mkdir ~/jhbuild; cd ~/jhbuild
    $ curl -o jhbuildrc-evince https://people.gnome.org/~gpoo/build/evince/jhbuildrc-evince
    $ git clone git://git.gnome.org/jhbuild
    $ (cd jhbuild; ./autogen.sh --simple-install; make install)

### OpenSUSE 12.3

The following steps have been tested to work well in Fedora 12.3 (GNOME edition) after a clean install.

Enable repository for source code packages:

    $ sudo zypper modifyrepo --enable repo-source

To install the basic dependencies:

    $ sudo zypper si -d evince gobject-introspection at-spi2-core libgtk-3-0
    $ sudo zypper install jhbuild gnome-common libexpat-devel gperf ragel cmake libgcrypt-devel icon-naming-utils libcroco-dev vala

Then, prepare to build Evince in `~/jhbuild`:

    $ mkdir ~/jhbuild; cd ~/jhbuild
    $ curl -o jhbuildrc-evince https://people.gnome.org/~gpoo/build/evince/jhbuildrc-evince

### Other distributions

For other distributions, you can use the equivalent of `apt-get build-dep`, `yum-builddep` or `zypper si -d`.  For more detailed steps, continue reading the following sections.

Building Evince and its dependencies
-------------------------------

Finally,  grab the configuration file for `jhbuild` and build the basic
dependencies for evince (poppler, a newer glib, evince itself, etc.):

    $ jhbuild -f jhbuildrc-evince
    $ mkdir -p ~/jhbuild/evince/install/etc/pango
    $ jhbuild -f jhbuildrc-evince run pango-querymodules > ~/jhbuild/evince/install/etc/pango/pango.modules
    $ jhbuild -f jhbuildrc-evince run evince

The source code will be downloaded to your `$HOME/jhbuild/evince/checkout` and
installed in `$HOME/jhbuild/evince/install`.

  [1]: http://projects.gnome.org/evince/
  [2]: http://git.gnome.org/browse/jhbuild
