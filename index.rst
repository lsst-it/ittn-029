:tocdepth: 1

Introduction
============

The current Teststand housed at NCSA is to be logically and physical relocated
to the base data center (BDC) in La Serena.  As the movement of hardware will be
inherently disruptive to ongoing development activities, we believe that a review
should be made of the requirements for the eventual Teststands that are
envisioned to be located both at the BDC and in Tucson.  This would allow use
to reevaluate and reallocate our current computing resources while identify any
equipment which needs to be procured. An interim Teststand plan will be needed
in order to maintain development while key equipment (E.g., a DAC) is in
transit.  Interim resources will need to be place prior to commencing tear down
at NCSA.

Rather than attempting to identically replicate the Teststand as it is
currently envisioned at NCSA, which would be labor intensive and require at
least some level of manual reconfiguration of each host, we plan to
re-provision each host from scratch upon arrival at the BDC.  This will necessitate
identifying data which needs to be preserved within the existing Teststand.
Instead of entrusting this data to to "snail mail", it should be copied in
advance via the long haul network (LHN).

It appears plausible that it would take ~3 months from the time a tear down is
commenced at NCSA until the hosts are again available for development usage at
the BDC. We believe this necessitates at least a functional auxtel Teststand in
Tucson and possibly the reallocation of resources at the BDC in order to
supplement the current Kueyen on Antu kubernetes clusters.  It is already known
that new equipment will be required in order to build a functional Teststand
environment in Tucson.  If the procurement process is started before the end of
September, 2020 it is conceivable that the new standard will be available prior
to the start of the CY 2020 "holiday season".  If NCSA is able to complete a
tear down and have equipment in transit over the "new year", it may help to
minimize the disruption as this is a period of time in which many staff are
expected to take leave.


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
