============
Preparations
============

In order to make a new release you will to prepare the image first.

.. contents:: :local:

Cleanup
-------

To clean and shrink we will do a bit of housekeeping::

    apt-get --purge -y clean
    apt-get --purge -y autoremove
    rm -f /var/cache/apt/archives/*.deb
    rm -f /var/cache/apt/*cache.bin
    rm -f /var/lib/apt/lists/*_Packages
    rm -f /etc/ssh/ssh_host_*

run above as root or with sudo

ToDo:
-----

- clear $USER history
- clear logfiles
