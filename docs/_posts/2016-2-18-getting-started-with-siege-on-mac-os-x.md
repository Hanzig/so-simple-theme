---
title: Getting started with Siege (Mac OS X)
categories:
  - tech
tags:
  - Siege
  - testing
---

I needed a proper tool to load test my Node.js application and do some
benchmarking. After doing some research, consulting some colleagues and trying some tools,
Siege was the one that I decided to use. Siege is an http/ftp load testing and benchmarking utility
designed for developers and administrators to measure the performance of their applications under load.

In this post I will go through the installation of this open-source software and get it ready for some load testing.

> Also, note that I used a MacBook Pro Retina with a 2,7 GHz Intel Core i5 processor and 16 GB 1867 MHz DDR3
for the installation as well as the tests and the following steps might not work on other operating systems.

If you already have ```autoconf```, ```automake``` and ```libtool``` installed on your machine, you can skip steps
1 - 3 and proceed.

1. **Install autoconf 2.69**

    Go to home directory:

    ```
    $ cd
    ```

    Download the source and decompress it:

    ```
    $ curl -O -L http://ftpmirror.gnu.org/autoconf/autoconf-2.69.tar.gz
    $ tar -xzf autoconf-2.69.tar.gz
    ```

    Go to the uncompressed folder:

    ```
    $ cd autoconf-2.69
    ```

    Run the ```configure``` script:

    ```
    $ ./configure
    ```

    Compile it with ```make```:

    ```
    $ make
    ```

    And install it:

    ```
    $ sudo make install
    ```

    If the version is ```autoconf 2.69```, then everything went fine:

    ```
    $ autoconf --version
    ```

2. **Install automake 1.15**

    Go to home directory:

    ```
    $ cd
    ```

    Download the source and decompress it:

    ```
    curl -O -L http://ftpmirror.gnu.org/automake/automake-1.15.tar.gz
    tar -xzf automake-1.15.tar.gz
    ```

    Go to the uncompressed folder:

    ```
    $ cd automake-1.15
    ```

    Run the ```configure``` script:

    ```
    $ ./configure
    ```

    Compile it with ```make```:

    ```
    $ make
    ```

    And install it:

    ```
    $ sudo make install
    ```

    If the version is ```automake 1.15```, then everything went fine:

    ```
    $ automake --version
    ```

3. **Install libtool 2.4.6**

    Go to home directory:

    ```
    $ cd
    ```

    Download the source and decompress it:

    ```
    curl -OL http://ftpmirror.gnu.org/libtool/libtool-2.4.6.tar.gz
    tar -xzf libtool-2.4.6.tar.gz
    ```

    Go to the uncompressed folder:

    ```
    $ cd libtool-2.4.6
    ```

    Run the ```configure``` script:

    ```
    $ ./configure
    ```

    Compile it with ```make```:

    ```
    $ make
    ```

    And install it:

    ```
    $ sudo make install
    ```

    Check ```libtool``` version

    ```
    $ man libtool
    ```

    If you see something like the following on the man page, then everything went well:

    ```
    libtool - manual page for libtool 2.4.6
    ```


4. **Clone Siege from GitHub**

    ```
    $ git clone https://github.com/JoeDog/siege.git
    ```

    Install the application:

    > IMPORTANT: If you are upgrading from an earlier version, you MUST delete
    the older version before installing this one. The simplest way to remove
    the older version to run "make uninstall" in the old source directory.
    If you no longer have the old source, you can configure the new version
    to be installed in the same place as the old version.  Then BEFORE you
    run "make install", run "make uninstall" first.

    ```
    $ cd siege
    $ utils/bootstrap
    $ make
    $ make install
    ```

    If you type

    ```
    $ siege --help
    ```

    and see a list of options, then Siege is ready to be used. For more details, make sure you read the INSTALL
    and README.md files that come with the software. More information can also be found on
    <a href="https://www.joedog.org/siege-home" target="_blank">https://www.joedog.org/siege-home</a>.

    In my <a href="/load-testing-with-siege">next post</a>, I'll load test a Node.js app and go through some
    of the options that Siege has to offer.
