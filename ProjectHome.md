<img src='http://weaknetlabs.com/linux/entify/images/entify-logo.png' />

Package management tool for Debian based OSes, including WEAKERTH4N and WarcarrierOS. The main goal of this project is to make a smaller live OS system by storing pre-compiled applications on the server for multiple platforms (e.g. CUDA environment, x86). As of now, the server side code packages are themed mostly as 802.11/802.15 wireless penetration testing tools most of which do not exist in deb format or in any default Debian aptitude repositories.

This tool is coded in Perl and requires only simple UNIX awk/sed/grep/wget/echo/tar functionality. It has also been tested only with Debian Wheezy environments.

### built-in functionality ###
  * checks if installed properly
  * simple install from argument `(--init|-i)`
  * update local list of packages from remote server with `(--update|-u)`
  * list packages with `(--list|-l)`
  * smart regular expressions for package manipulation
  * smart-low bandwidth package manipulation
  * all cache and system files in centralized location: /etc/entify
  * keeping track of installed application using the same configuration file with smart regular expressions
  * simple and easy cache manipulation from command line arguments
  * complete uninstall from simple command-line arguments
  * smart "uninstall" feature even for applications whose author's didn't write and uninstall script - each by hand.

Example output:
```
warcarrier:/appdev/entify# ./entify 

 Entify - WeakNet Labs Package Manager

 --init		Run setup and initialize files
 --update	Update file list from remote server
 --list		List all installable packages from remote server
 --give-me	Install package from remote server sources
 --remove	Remove package
 --help		This help
 --clean	Clean out cached source and tar files
 -x		Remove all Entify files and sources

warcarrier:/appdev/entify# ./entify -i
[ * ] Initializing Entify for your environment
[ + ] Creating install directory /etc/entify
[ * ] Retrieving latest list
[ * ] Updating list for installed packages
[ + ] Adding Files
[ * ] Initialization completed

warcarrier:/appdev/entify# ./entify -l
gpsd-3.2 - service daemon that monitors one or more GPSes
aircrack-ng-1.1-r2279 - 802.11 Penetration testing suite of tools
wbar-2.3.4 - Just a simple and highly customizable quick-launch tool
freeradius-server-2.1.11 - demonstrate RADIUS impersonation vulnerabilities
airpwn-1.4 - Airpwn is a framework for 802.11 (wireless) packet injection
reaver-1.4 - Reaver implements a brute force attack against Wifi Protected Setup
cowpatty-4.3 - Brute-force dictionary attack against WPA-PSK
kismet-2013-03-R1b - 802.11 layer2 wireless network detector sniffer and intrusion detection system
---------------------
[ * ] 7 Total packages
[ * ] 0 Installed

warcarrier:/appdev/entify# ./entify -g wbar
[ * ] Adding package: wbar
[ + ] Getting source for wbar-2.3.4 from remote server, this may take some time.
[ * ] Package is here, uncompressing.
/appdev/entify
[ * ] Running make install
[ * ] Checking rules
[ + ] Package has dependencies, installing: libglade2-dev libimlib2-dev intltool
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libimlib2-dev is already the newest version.
intltool is already the newest version.
libglade2-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
warcarrier:/appdev/entify# ./entify -d freeradius
freeradius-server-2.1.11
-----------------------
Size: 13M
URL: http://www.willhackforsushi.com/?page_id=37
Description: demonstrate RADIUS impersonation vulnerabilities

warcarrier:/appdev/entify# ./entify -d cowpatty
cowpatty-4.3
-----------------------
Size: 432K
URL: http://www.willhackforsushi.com/Cowpatty.html
Description: Brute-force dictionary attack against WPA-PSK

warcarrier:/appdev/entify#
```