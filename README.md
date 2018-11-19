# tungsten-resource-test
Shaker tests intended for eventual incorporation into CI testing

Overview
===============
The tests provided in this repo work are a copy of the Contrail tests used internally at AT&T.

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

Execute Shaker per the documentation e.g. create a shaker.cfg and shaker --config-file shaker.cfg
