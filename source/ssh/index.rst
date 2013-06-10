====
SSH
====

.. contents:: :local:


To create ssh keys on first boot change */etc/init/ssh.conf* to

.. code::

        # ssh - OpenBSD Secure Shell server
        #
        # The OpenSSH server provides secure shell access to the system.

        description     "OpenSSH server"

        start on filesystem or runlevel [2345]
        stop on runlevel [!2345]

        respawn
        respawn limit 10 5
        umask 022

        # 'sshd -D' leaks stderr and confuses things in conjunction with 'console log'
        console none

        pre-start script
                test -x /usr/sbin/sshd || { stop; exit 0; }
                test -e /etc/ssh/sshd_not_to_be_run && { stop; exit 0; }
                test -c /dev/null || { stop; exit 0; }

        #ssh keys:
        test -f /etc/ssh/ssh_host_dsa_key || dpkg-reconfigure openssh-server

        mkdir -p -m0755 /var/run/sshd
        end script

        # if you used to set SSHD_OPTS in /etc/default/ssh, you can change the
        # 'exec' line here instead
        exec /usr/sbin/sshd -D

That will test the existence of host keys, and regenerate them if they are not present.

Before stopping your template guest, delete the ssh host keys::

        rm -f /etc/ssh/*host*key*

