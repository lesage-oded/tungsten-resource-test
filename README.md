# tungsten-resource-test
Shaker tests intended for eventual incorporation into CI testing

Overview
===============
The tests provided in this repo work using a patched version of Shaker to add enhancements necessary to run the tests.
These enhancements include the ability to specify supporting heat stacks for a test and use heat environment files.

Setup
------------------

Clone Shaker repo:

- git clone https://github.com/openstack/shaker.git

Apply AT&T enhancement patch:
 - cd shaker
 - git apply -v path/to/patch/in/this/repo/att-shaker.patch
 - ***** if the patch does not apply cleanly:
    - As of this writing the latest commit hash in the Shaker repo is d549718a68380d9fc004a64a80416b97844f9d53
    - If the patch does not apply cleanly you can:
       - git reset --hard (commit hash above)
	   - reapply patch

Once the patch is applied cleanly you should be able to execute the Contrail tests provided in this repo per the usual Shaker directions
e.g. create a shaker.cfg which uses the tests provided in this repo.

