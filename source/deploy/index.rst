=============
Deploy Image
=============

.. contents:: :local:

Prepare
--------

In order to depoly an new build we have to prepare some things first to make sure that the image is clean.

Clean ssh::

    sudo rm -f /etc/ssh/*host*key*

Networking::

    sudo rm -f /etc/udev/rules.d/70-persistent-net.rules

Clean apt::

    apt-get autoclean
    apt-get clean

History::

    sudo history -c
    rm -rf /home/zopeuser/.bash_history
