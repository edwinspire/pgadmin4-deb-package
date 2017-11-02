pgAdmin4 Debian Package!
===================

**pgAdmin** is the most popular and feature rich Open Source administration and development platform for PostgreSQL, the most advanced Open Source database in the world.

This is a package that can be modified for the version of **pgAdmin4** you want.
Using **fakeroot** en Debian you can convert it into a **.deb** installer package.

----------


Create Debian Package
-------------

 Download the zip file (and unzip) or clone this repository.
Open a terminal as root and run:
 `fakeroot dpkg -b  /here/the/path/to/the/downloaded/pgadmin4-deb-package/pgadmin4-x.x `

This should create a debian installer.

    pgadmin4-x.x.deb

 Install it using dpkg, apt-get or your favorite installer.


 To start pgAdmin4 you must run as administrator:

    python /usr/local/lib/python2.7/dist-packages/pgadmin4/pgAdmin4.py


The application will ask for an email and a password, which they must use to access.


Finally you can access pgAdmin4 at the following address:

    http://localhost:5050

----------
Remote access
-------------
By default pgAdmin4 only allows local access from the browser, if you want to access remotely you can do so by editing the configuration file.

This installation creates by default a file **usr/local/lib/python2.7/dist-packages/pgadmin4/config_local.py** where **DEFAULT_SERVER** = '0.0.0.0' has been modified to be able to access pgAdmin4 remotely. You can delete this file if you do not want that feature. 

----------
pgAdmin4 as service (Daemon)
-------------
Before configuring as a service you must run pgadmin4 and verify that you can access from the browser without problem.

For **systemd**, this installation will automatically create the file **/etc/systemd/system/pgadmin4.service** 

You have to enable it manually if you want the service to start at the beginning of the system, with the following command as root:

    systemctl enable pgadmin4

You can start the service with the following command:

    systemctl start pgadmin4

To see the service log, do it with the following command:

    journalctl -u pgadmin4

----------
> **Note:**

> - You must have all package dependencies installed before you begin.
> - In case of problems with dependencies you can execute **apt-get install -f**
