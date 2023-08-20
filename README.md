Rebuild QEMU KVM on Centos 8
============================

Step 1: Set up build environment
--------------------------------

https://wiki.centos.org/HowTos/SetupRpmBuildEnvironment


Step 2: Download source
-----------------------

The qemu tarball is too big for github, so download separately:

    cd ~/rpmbuild/SRPMS
    dnf download --source qemu-kvm
    cd ~/rpmbuild/SOURCES
    rpm2cpio ~/rpmbuild/SRPMS/qemu-kvm-6.2.0-35.module_el8+466+00f6f2b0.src.rpm | cpio -idmv
 

Step 3: Build
-------------

Build the RPMs:

    cd ~/rpmbuild/SPECS
    yum-builddep qemu-kvm.spec
    rpmbuild -ba qemu-kvm.spec
