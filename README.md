# tungsten-resource-test
Shaker tests intended for eventual incorporation into CI testing

Overview
===============
The tests provided in this repo work using a patched version of Shaker to add enhancements necessary to run the tests.
These enhancements include the ability to specify supporting heat stacks for a test and use heat environment files.

Setup
------------------

Prepare Glance Image:

The qcow2 image which contains necessary tools, like bridgeutils, for certain Contrail tests has been split
to accommodate the file size imposed by github. It can be rejoined and verified with:

  - cd qcow2
  - cat shaker-part.0* > shaker-image.qcow2
  - md5sum -c shaker-image.manifest

You can then upload shaker-image.qcow2 into Glance

Clone Shaker repo:

- git clone https://github.com/openstack/shaker.git

Apply AT&T enhancement patch:
 - cd shaker
 - git apply -v path/to/patch/in/this/repo/att-shaker.patch
 - ***** if the patch does not apply cleanly:
    - As of this writing the latest commit hash in the Shaker repo is abe9fbd877bc0114896b17e8c36b3fa6d71c7d02
    - If the patch does not apply cleanly you can:
       - git reset --hard (commit hash above)
	   - reapply patch

Once the patch is applied cleanly, and shaker-image.qcow2 has been uploaded to Glance, you should be able to execute 
the Contrail tests provided in this repo per the usual Shaker directions e.g. create a shaker.cfg which uses the tests provided in this repo.

