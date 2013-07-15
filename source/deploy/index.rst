=============
Deploy Image
=============

.. contents:: :local:

Depoyment
---------

After you followed all steps on :doc:`../prepare_image/index` you are now ready to deploy a new build.

* Shut down the VM

Clone the VMDK
--------------

VirtualBox only lets you compact VDIs, but if we clone a VMDK we get a compressed copy. So find your disk image::

    cd $VirtualBox_VMs_dir/$vm_dir

If you don’t have any snapshots, just::

    VBoxManage clonehd $disk_name.vmdk clone.vmdk

Otherwise, find the snapshot you want. I just want the newest one, so I::

    ls -lt Snapshots

And I get something like this at the top (newest file is on top)::

    -rw------- 1 force force 721092608 Jul 12 10:13 {11f18f3d-9a0b-4e98-b680-a108ac31a0aa}.vmdk

The 11f18f3d... is the UUID. So I want to use that to clone the disk.::

    VBoxManage clonehd 11f18f3d-9a0b-4e98-b680-a108ac31a0aa clone.vmdk
