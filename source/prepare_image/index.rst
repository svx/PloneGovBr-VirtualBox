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

Run above as root or with sudo.

Empty all the logs in a directory::

    for i in /var/log/*; do cat /dev/null > $i; done

As normal user, clean history and ssh::

    rm -rf ~/.bash_history

Further we need to delete the ssh folder of the user, this we will do at the
end::

    ssh -t $USER@$IP 'rm -rf ~/.ssh/*'
    

Shrink the image
----------------

Try filling the unused space with zeros to make for better compression. The
catch here is that if your VM has a big disk, this could take a while. Also,
you'll want to do this right before you package it up for distribution.::

    cat /dev/zero > zero.fill;sync;sleep 1;sync;rm -f zero.fill


