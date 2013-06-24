Pilbox
======

Pilbox is an image resizing application built on Python's [Tornado web framework](http://www.tornadoweb.org/en/stable/) using the [Python Imaging Library (PIL)](http://www.pythonware.com/products/pil/). It is not intended to be the primary source of images, but instead acts as a proxy which requests images, resizes them to the desired size and optionally stores the resized version.

Setup
=====

Dependencies
------------

  * [Python 2.7](http://www.python.org/download/)
  * [PIL 1.1.7](http://www.pythonware.com/products/pil/)
  * [python-magic 0.4.3](https://pypi.python.org/pypi/python-magic/)
  * [tornado 3.1](https://pypi.python.org/pypi/tornado/3.1)
  * Image Libraries: libjpeg-dev, libfreetype6, libfreetype6-dev, zlib1g-dev

Vagrant
-------

Packaged with Pilbox is a [Vagrant](http://www.vagrantup.com/) configuration file which installs all necessary dependencies on a virtual box. See the [Vagrant documentation for installation instructions](http://docs.vagrantup.com/v2/installation/). Once installed, the following will start a virtual machine.

    $ vagrant up

To access the virtual machine itself, simply...

    $ vagrant ssh

Running
=======

To run the application, issue the following command

    $ python pilbox/app.py

By default, this will run the application on port 8888 and can be accessed by viisting:

    http://localhost:8888/

If running via Vagrant, you will need to determine virtual machine's IP address.

    $ vagrant ssh
    $ /sbin/ifconfig -a

To see a list of all available options, run

    $ python pilbox/app.py --help

Testing
=======

To run all tests, issue the following command

    $ python -m pilbox.test.runtests

To run individual tests, simply indicate the test to be run, e.g.

    $ python -m pilbox.test.runtests pilbox.test.signature_test

Tools
=====

To verify that your application is generating correct signatures, use the signature command

    $ python -m pilbox.signature --key=abcdef "x=1&y=2&z=3"
    Query String: x=1&y=2&z=3
    Signature: 971cdc08caac8b9196862914d25fd3e4
    Signed Query String: x=1&y=2&z=3&sig=971cdc08caac8b9196862914d25fd3e4
