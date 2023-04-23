Aquaplanet with a fixed SST
+++++++++++++++++++++++++++
Now that you've ported CESM successfully to Keeling and have been able to validate your port and run some example tests, 
where do you start? With this example, hopefully you can get a sense for how you can adjust parameters within CESM and run tests.

This tutorial assumes you've been able to complete :ref:`porting<port_cesm>` and :ref:`out of the box capability<out_of_box_cesm>`.

Introduction
=============
An aquaplanet component set is typically an atmosphere only model where it's assumed that the Earth is a ball of water with no land and usually no sea ice. This simplified model can help us parse atmospheric interactions with the surface ocean very easily.

Here, we'll be going over how to change the sea surface temperature in order to see how the atmosphere is disturbed.

This tutorial partially follows the :ref:`UCAR example for the CAM5 physics model<https://www.cesm.ucar.edu/models/simple/aquaplanet>`.

Creating a new case
====================
Like usual, you'll want to start with creating a case in ``cesm1.2.1/scripts``:

``./create_newcase -case aqua_testperturb -compset FC5AQUAP -res f19_f19 -mach keeling``

* **case aqua_testperturb**: This is the case name, which you can set to anything. Here, it's aqua_testperturb
* **compset FC5AQUAP**: This is the component set. We're using the CAM5 aquaplanet compset.
* **res f19_f19**: Our resolution. Ours is around 2 deg. x 2 deg.
* **mach keeling**: Our machine that we set up here <out_of_box_cesm>.

Changing the sea surface temperature
=====================================
For the purposes of this example, we want to change our sea surface temperature (which is fixed throughout the whole simulation) so that it's slightly hotter at the equator, like below. (Plotted with Python)

.. image:: 
