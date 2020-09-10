:tocdepth: 1

Collect Information
===================

Identify hardware which needs to be relocated
---------------------------------------------

* Create a manifest of AURA inventory tags, Dell service tags, and the BMC and
  first interface MAC addresses.

Identify users impacted
-----------------------

Identify who is currently using the teststand and will be impacted by a move.

Identify data which needs to be presevered
------------------------------------------

All important data must be identified and transfered in advance via the
network.  We should not assume that equipment will free from damage while being
handled twice and in transit.  It may be convenient to also identify any data
which needs to be regularly backed as part of this audit.

========= =================== =====
What      Where               Size
========= =================== =====
EFD data  ``lsst-l1-cl-efd``  ~1TiB
========= =================== =====

Data Transfer
=============

Identify resources within the BDC for data storage and coordinate with NCSA for
data transfers.  Where possible, a digest should be used to verify the
integrity of the copy.

Transition Schedule
===================

It is estimated that teststand hardware will be unavailable for ~3 months
starting from the point at which the transfer of any data which needs to be
preserved is complete and the "Interium Teststand(s)" are avaiable.

============================== =============
Activity                       Time Estimate
============================== =============
tear down and packaging @NCSA  2 weeks
in transit to La Serena        2-3 weeks
pallets moved into BDC         1 week
racking and stacking @BDC      2 weeks
provisioning                   2 weeks
schedule slack                 2 weeks
total                          11-12 weeks
============================== =============


Interium Teststand(s)
=====================

The transition is inherently going to be disruptive of current activities.
Alternative resources to support on going development needs to be identified
and in place prior to the start of tear down @NCSA.  This may need to be a
combination of rescheduling activities, reallocation of existing resources in
Tucson and/or the BDC, acquisition of new resources, or making use of public
cloud(s).


Physical Shipment
=================

Packing materials, shipment logistics, and scheduling labor will need to be
coordinated with and largely lead by NCSA.


Define Teststand(s) to be located at the BDC
============================================

Test environments
-----------------

===== =======
Name  Purpose
===== =======
TBD
===== =======

Installation of Teststand(s)
============================

Replace disks
-------------

Cabinet Layout
--------------

The foot print of the systems is expected to be 2-3 48U cabinets.  The number
of management and access ports is TBD.

Spares
------

As we expect that the warranty either has or will soon expire an many of the
systems being migrated, ~10% should be reseved as online "hot spares" and/or to
be canibalized for parts.


Provisioning
============

The intent is that the vast majority of systems will be re provisioned from
scratch. This will likely involve resetting the BMC and system BIOS/EFI back to
factory defaults from a local console.  All teststand nodes are to be attached
to the LS foreman instance. If there multiple independent Teststands, they may be
configured as separate foreman "locations" as a means of isolating
administrative access.
