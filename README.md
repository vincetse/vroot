What is `vroot`?
----------------

Have you ever wished you had clean Linux environments of the different versions of your Debian or Ubuntu distribution that you can create quickly and then blow it away just as easily without having to resort to building a virtual machine?  A `chroot` is the way to go!  `vroot` is a set of scripts that helps you conveniently create, manage and use a `chroot`.

This project was inspired by the `yroot` utility at Yahoo, so you (former) Yahoos may find this familiar.


Supported Linux Distributions
-----------------------------

This utility only works on Debian and Ubuntu at this point.  I have used a derivative it on CentOS before but lost that version of the script.  I will toss one together again some time, or you can send me a patch.


Configuration
-------------

The configuration file, `~/.vrootrc`, will be created if you do not already have one.  The following is a sample.

    #
    # the location where your vroots will live
    #
    VROOT_BASE=${HOME}/.vroot
    
    #
    # the default architecture to build vroots in if none is specified
    #
    VROOT_DEFAULT_ARCHITECTURE=amd64
    
    #
    # the default codename to build vroots with if none is specified
    #
    VROOT_DEFAULT_CODENAME=squeeze

    #
    # the default distribution to build vroots with if none is specified
    #
    VROOT_DEFAULT_DISTRIBUTION=Debian

Installation
------------

There is no installation script.  You can just copy all the files to a directory in the path and start using them.


Usage
-----

Creating a new `vroot`
======================

A new `vroot` can be created with the `vroot_create` utility.  Run it with the `--help` parameter to see its help page.

    vt100x@dev01:~/bin
    $ vroot_create --help
    
    vroot_create [options] <vroot_name>
    
        -h|--help       prints this page
        -a|--arch       architecture, i386 or amd64 [default: amd64]
        -d|--distro     distribution, Ubuntu or Debian [default: Debian]
        -c|--codename   codename of the version [default: squeeze]

The default values for the parameters are set in the configuration file.

Using a `vroot`
===============

Simple!  Run `vroot <vroot_name>` at the command line.


What `vroot`s do I have?
========================

`vroot_list` shows you what `vroot`s have been created.

How do I delete a `vroot`?
==========================

The best way to delete a `vroot` is do reboot your machine, then delete the directory of the `vroot`.  Rebooting is a good idea if you have used that `vroot` because directories might have been mounted in it.

References
----------

1. https://wiki.ubuntu.com/DebootstrapChroot
2. http://jblevins.org/log/ubuntu-chroot
