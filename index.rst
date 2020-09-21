:tocdepth: 1

Introduction
============

The current Teststand housed at NCSA is to be logically and physical relocated
to the base data center (BDC) in La Serena.  At a minimum, the "full size" DAQ
will have to be physically moved.  The relocation may be achieved by purchasing
new servers, moving existing servers or a combination of the two.  There are
capital cost and schedule impacts with either approach which need to be
weighed. As the movement of hardware will be inherently disruptive to ongoing
development activities, we believe that a review should be made of the
requirements for the eventual Teststands that are envisioned to be located both
at the BDC and in Tucson.  This would allow use to reevaluate and reallocate
our current computing resources while identifying any equipment which needs to
be procured. An interim Teststand plan will be needed in order to maintain
development while key equipment (E.g., a DAC) is in transit.  Interim resources
will need to be place prior to commencing tear down at NCSA.

Rather than attempting to identically replicate the state of hosts in the
Teststand as it is currently envisioned at NCSA, which would be labor intensive
and require at least some level of manual reconfiguration of relocated hosts,
we plan to re-provision any migrated host from scratch upon arrival at the BDC.
This will necessitate identifying data which needs to be preserved within the
existing Teststand.  Instead of entrusting this data to to "snail mail", it
should be copied in advance via the long haul network (LHN).

It appears plausible that it would take ~3 months from the time a tear down is
commenced at NCSA until a relocate host would again be available for
development usage at the BDC.  The time table is closer to ~5 months for
relocating a DAQ.  We believe this necessitates at least a functional
auxtel/comcam Teststand in Tucson and possibly the reallocation of resources at
the BDC in order to supplement the current Kueyen on Antu kubernetes clusters.
It is already known that new equipment will be required in order to build a
functional Teststand environment in Tucson.  If the procurement process is
started before the end of September, 2020 it is conceivable that the new
standard will be available prior to the start of the CY 2020 "holiday season".
If NCSA is able to complete a tear down and have equipment in transit over the
"new year", it may help to minimize the disruption as this is a period of time
in which many staff are expected to take leave.

This is intended sequence of steps to plan and execute a teststand relocation:

* Collect Information
* Define Teststand(s)
* Transfer Data to BDC
* Establish Interim Teststand(s)
* Ship to and/or order for the BDC
* Install hardware
* Provision hardware

Collect Information
===================

Identify hardware which needs to be relocated
---------------------------------------------

.. raw:: html

   <s>

Create a manifest of AURA inventory tags, Dell service tags, and the BMC and
first interface MAC addresses.

.. raw:: html

   </s>

* `NCSA Test Stand Configuration (confluence) <https://confluence.lsstcorp.org/display/LSSTCOM/NCSA+Test+Stand+Configuration>`_
* `Manifest created by Bill Glick <https://docs.google.com/spreadsheets/d/13x9k6B36t5i45mAN6YvDYasW0LVtuF6NNW5x1qleno4/edit#gid=0>`_

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

Servers
-------

============================== =============
Activity                       Time Estimate
============================== =============
tear down and packaging @NCSA  2 weeks
transit NCSA -> Tucson         1 week
transit Tucson -> La Serena    2-3 weeks
pallets moved into BDC         1 week
racking and stacking @BDC      2 weeks
provisioning                   2 weeks
schedule slack                 2 weeks
total                          12-13 weeks
============================== =============

DAQ(s)
------

============================== =============
Activity                       Time Estimate
============================== =============
tear down and packaging @NCSA  2 weeks
transit NCSA -> SLAC           1 week
time at SLAC                   8 weeks
transit SLAC -> Tucson         1 week
transit Tucson -> La Serena    2-3 weeks
pallets moved into BDC         1 week
racking and stacking @BDC      1 week
provisioning                   1 week
schedule slack                 2 weeks
total                          19-20 weeks
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

DAQ(s)
------

The DAQ(s) will need to take a different course from the servers and first be
from NCSA directly to SLAC for a firmware upgrade and to debug interface
errors.  Once these tasks are complete, the DAQ(s) will be shipped to Tucson to
be sent on to La Serena.


Shipment Cost Estimate
----------------------

Assumptions:

* ~50 servers total
* On average, a server will fit in a 1'x2'x3' box / 6 ft^3 per server
* On average, the combined weight of server + packaging will be 75lbs or less.
* 1 "dimensional lbs" == 139"^3

Estimated Weight/Volume:

======= ==========
Unit    value
======= ==========
weight  3750 lbs
volume  300 ft^3
======= ==========

Per the Tucson Logistics and Property Supervisor 2020-09-15: Fedex Ground is
~$10 per server for shipping from IL to AZ.

Cost NCSA -> Tucson: ~$500

Per the Tucson Logistics and Property Supervisor 2020-09-15: Air freight from
Tucson to La Serena is $6 per dimensional lb.

Cost Tucson -> La Serena:

====================== ==========
Cost basis             $
====================== ==========
By weight              ~$22,500
By dimensional weight  ~$22,377
====================== ==========

This company sells 1U and 2U server shipping boxes for $125/ea delivered:

https://www.servershippingbox.com/

Which would work out to a charge of $6,250 to buy all new boxes.

Cost Summary:

==================== ===========
Item                 Cost
==================== ===========
NCSA -> Tucson       ~$500
Tucson -> La Serena  ~$22,500
Packaging Materials  ~$6,250
Total                ~$29,250
==================== ===========


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
be cannibalized for parts.


Provisioning
============

The intent is that the vast majority of systems will be re provisioned from
scratch. This will likely involve resetting the BMC and system BIOS/EFI back to
factory defaults from a local console.  All teststand nodes are to be attached
to the LS foreman instance. If there multiple independent Teststands, they may be
configured as separate foreman "locations" as a means of isolating
administrative access.
