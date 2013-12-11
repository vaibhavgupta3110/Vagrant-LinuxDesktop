Vagrant's Ubuntu 12.04 Desktop Environment for Windows
=

## Overview

Many unsatisfied Windows users find themselves yearning for more. Yet, they don't have the cash flow to pick up a Linux box or the technical expertise to create a partition on their local hard drive, from which to boot an Ubuntu Desktop environment. Well, ladies 'n gentlemen ... drum roll, please ...

## Purpose

To provide a simple way for Windows users to create a Linux sandbox on their local machine.

### What is Vagrant?

[Vagrant](http://www.vagrantup.com) is a "tool for building and distributing development environments". It works with [virtualization](http://en.wikipedia.org/wiki/X86_virtualization) software such as [VirtualBox](https://www.virtualbox.org/) to provide a virtual machine that is sandboxed away from your local environment.

## How to Use

1. Start with any operating system.
>If you are new to the wonderful world of `git` (version control), it's advisable to download [GitHub for Windows](http://windows.github.com/) or [GitHub for Mac](http://mac.github.com/).
1. Install the most recent release of [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
1. Once VirtualBox is installed, also install the corresponding [VirtualBox Extension Pack](https://www.virtualbox.org/wiki/Downloads).
1. Install the most recent release of [Vagrant](http://www.vagrantup.com/downloads.html)
    * `vagrant` will now be available as a command in your terminal, try it out.
    * ***Note:*** If Vagrant is already installed, use `vagrant -v` to check the version. You may want to consider upgrading if a much older version is in use.
1. Clone or extract the _Vagrant's Ubuntu 12.04 Desktop Environment for Windows_ project into a local directory
    * `git clone git://github.com/vDevices/Vagrant-UbuntuDesktop.git vagrant-ubuntu-desktop`
    * OR download and extract the repository master [zip file](https://github.com/vDevices/Vagrant-UbuntuDesktop/archive/master.zip)
1. Change into the new directory with `cd vagrant-ubuntu-desktop`

#### The First `Vagrant Up`

1. Start the Vagrant environment with `vagrant up`
    * Be patient as the magic happens. This could take a while on the first run as your local machine downloads the required files.

### What Did That Do?

The first time you run `vagrant up`, a packaged box containing a basic virtual machine is downloaded to your local machine and cached for future use. The file used by `Vagrant's Ubuntu 12.04 Desktop Environment for Windows` contains an installation of Ubuntu 12.04.

After this box is downloaded, it begins to boot as a sandboxed virtual machine using VirtualBox. Once booted, it runs the included provisioning script, to install the Ubuntu desktop environment.

The time for all of this to happen depends a lot on the speed of your Internet connection. If you are on a fast cable connection, it will likely only take several minutes.

On future runs of `vagrant up`, the packaged box will be cached on your local machine and Vagrant will only need to apply the requested provisioning.

* ***Preferred:*** If the virtual machine has been powered off with `vagrant halt`, `vagrant up` will quickly power on the machine without provisioning.
* ***Rare:*** If you would like to reapply the provisioning scripts with `vagrant up --provision` or `vagrant provision`, some time will be taken to check for updates and packages that have not been installed.
* ***Very Rare:*** If the virtual machine has been destroyed with `vagrant destroy`, it will need to download the full 100MB of package data on the next `vagrant up`.

### Now What?

Now that you're up and running, start poking around and modifying things.

1. Access the server via the command line with `vagrant ssh` from your `vagrant-local` directory. You can do almost anything you would do with a standard Ubuntu installation on a full server.
    * If you are on a Windows PC, you may need to install additional software for this to work seamlessly. A terminal program such as [Putty](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html) will provide access immediately.
1. Destroy the box and start from scratch with `vagrant destroy`
    * As explained before, the initial 280MB box file will be cached on your machine. the next `vagrant up` command will initiate the complete provisioning process again.
1. Power off the box with `vagrant halt` and turn it back on with `vagrant up`.
1. Suspend the box's state in memory with `vagrant suspend` and bring it right back with `vagrant resume`.
1. Reapply provisioning to a running box with `vagrant provision`.

## Need Help?

* Open a new [Issue](https://github.com/vDevices/Vagrant-UbuntuDesktop/issues) on GitHub if you run into trouble or have any suggestions.
* Vagrant has a [Mailing List](https://groups.google.com/forum/#!forum/vagrant-up) for any topic related to Vagrant (that is a great place to get started).

## Credits

A HUGE `Thank You` is in order to:

* [Portal Stack: Vagrant + VirtualBox + Ubuntu for linux development](http://portalstack.blogspot.com/2013/11/vagrant-virtualbox-ubuntu-for-linux.html) | By [Mike Kunze](https://github.com/mikekunze?tab=repositories) (for planting the seeds for this idea); and
* The trailblazers at the successful [Varying Vagrant Vagrants](https://github.com/10up/varying-vagrant-vagrants)
