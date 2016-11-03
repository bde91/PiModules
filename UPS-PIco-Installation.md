# UPS PIco Installation Guide

## Update System & Download Packages

The UPS PIco utilises a Daemon (background process) to manage function, which requires setup prior to installation and use of the UPS PIco. This Daemon includes the email broadcasting system for PIco email alerts.

The UPS PIco is designed to operate on Raspian or other Operating Systems (OS) based on this platform. The UPS PIco has been tested on Raspian - Release date:2016-09-23, Kernel version:4.4. We cannot guarantee that the system will work on versions of Raspian previous to this, so please ensure that your OS is fully up to date by running the following update commands before attempting to install the UPS PIco.

First, update your system's package list:

    sudo apt-get update

Next, upgrade all your installed packages to their latest versions:

    sudo apt-get dist-upgrade

Next, ensure that Python is installed and updated, by using the following command:

    sudo apt-get install python-rpi.gpio

And update the following Python packages:

    sudo apt-get install git python-dev python-serial python-smbus python-jinja2 python-xmltodict python-psutil python-pip

Next, clone the Raspberry Pi daemons and email broadcasting system from the GitHub using the following command:

    sudo git clone https://github.com/modmypi/PiModules.git

This will clone the PiModules Git to your Raspberry Pi home directory.

## Install the Email Broadcasting Package:

Move to the PiModules git "package" folder:

    cd PiModules/code/python/package

Then proceed with the installation of the email package software

    sudo python setup.py install

**More information about the package usage and details are available at https://github.com/modmypi/PiModules**

## Install the System Monitoring & File Safe Shutdown Daemons

Move to the PiModules git "upspico/picofssd" folder:

    cd PiModules/code/python/upspico/picofssd
