Porting CESM
============

Modules
---------

First off, in order to have CESM building and running correctly, write the following lines into a file called $HOME/.modules7 ($HOME should be your home directory)

These modules ensure that the right compilers and MPI library are running when you run CESM.

.. code-block:: console
   module load intel/intel-15.0.3
   module load intel/hdf5-1.10.6-intel-15.0.3
   module load intel/netcdf4-4.7.4-intel-15.0.3
   module load intel/openmpi-4.1.2-intel-15.0.3 

You might need to log into Keeling again for these to work.

Checking out and downloading the model
---------------------------------------

Make a directory for your CESM modes: ``mkdir CESM``

``cd CESM``

Checking out the model: ``svn co https://svn-ccsm-models.cgd.ucar.edu/cesm1/release_tags/cesm1_2_1 cesm1_2_1``

* This downloads cesm1_2_1 to a directory called cesm1_2_1 in the current directory.
* When prompted for password for ``'<keeling_account>':`` put in your password for your keeling account.
* When prompted for username afterwards, input "guestuser" and password "friendly". This will happen a couple times.
* The system will then ask "Store password unencrypted?". Type "yes". This will occur several times.

When this message pops up, type "p":
.. code-block:: console
   > Error validating server certificate for 'https://svn-homme-model.cgd.ucar.edu:443':
    - The certificate is not issued by a trusted authority. Use the fingerprint to validate the certificate manually!
   Certificate information:
    - Hostname: *.cgd.ucar.edu
    - Valid: from Wed, 17 Nov 2021 00:00:00 GMT until Sun, 18 Dec 2022 23:59:59 GMT
    - Issuer: InCommon, Internet2, Ann Arbor, MI, US
   - Fingerprint: 35:da:70:4d:b6:cf:01:a3:fc:c2:63:6f:eb:15:de:81:fc:18:69:e3

   - > (R)eject, accept (t)emporarily or accept (p)ermanently? p

