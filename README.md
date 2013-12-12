Vagrant's Linux Desktop Environment for Windows &amp; Mac
=

By: [Pablo Carranza](https://plus.google.com/107285164064863645881?rel=author) | [vDevices](http://vdevices.com/)

### This Project's Purpose

To provide a simple way for Windows &amp; Mac users to launch a virtual machine ("VM") with a Linux Desktop environment &ndash; sandboxed on their local computer.

### Contributing

Contributions are more than welcome. Please submit [Pull Requests](https://github.com/vDevices/Vagrant-LinuxDesktop/pulls) against the master branch. For more information on the topic of Pull Requests, consult the [GitHub Help](https://help.github.com/) section on [Collaborating](https://help.github.com/categories/63/articles).

## Introduction

For many years, there were barriers surrounding the many unsatisfied Windows users finding themselves yearning for more and Mac OS X users that developed an itch for tinkering with open-source tools. Namely, they didn't have:

* the cash-flow or desire to pick up a dedicated Linux box; or
* the technical expertise to create a dual-boot environment &ndash; that is, a partition on their local hard drive, from which to boot a Linux Desktop environment.

Well, ladies 'n gentlemen ... drum roll, please ...

## Meet Vagrant

[Vagrant](http://www.vagrantup.com) is a cross-platform, open-source tool for building and distributing computing environments. It works with [virtualization](http://en.wikipedia.org/wiki/X86_virtualization) software such as [VirtualBox](https://www.virtualbox.org/) to provide a virtual machine (on your local Mac or Windows PC) that is sandboxed, or sectioned-off, from your local environment.

## Meet VirtualBox

VirtualBox is also a cross-platform, open-source "[virtualization](https://www.virtualbox.org/wiki/Virtualization) product for enterprise as well as home use." VirtualBox is installed on an existing **host** operating system ("OS") as an application &ndash; such as on your local Windows or Mac computer. VirtualBox, while running as an application on your computer, then allows an additional **guest** OS to be loaded and run, within its own virtual environment.

Thus, VirtualBox can be used to run a virtual Linux computer on your Mac or Windows PC. While Vagrant saves you the trouble of having to build a guest OS from scratch; by simply downloading a pre-packaged virtual machine running a particular guest OS, named a [vagrant box](http://docs.vagrantup.com/v2/boxes.html). Other possible VirtualBox configurations (although, outside the scope of this project) are:

* Run a Windows 7, or Windows XP, VM on a Windows 8 machine;
* Run Max OS X on Windows;
* Run Windows programs and, consequently, the Windows OS, on a Mac;
* And more!

## How to Use

1. Start with any operating system ("OS").

	>If you are new to the wonderful world of `git` (version control) &ndash; and/or are uncomfortable with the command line &ndash; download [GitHub for Windows](http://windows.github.com/) or [GitHub for Mac](http://mac.github.com/).
2. Install the most recent release of [VirtualBox](https://www.virtualbox.org/wiki/Downloads), for your OS.
	>Once VirtualBox is installed, also install the corresponding [VirtualBox Extension Pack](https://www.virtualbox.org/wiki/Downloads).
3. Install the most recent release of [Vagrant](http://www.vagrantup.com/downloads.html), for your OS.
    * `vagrant` will now be available as a command in your command prompt or terminal.
		* **Microsoft Windows users:** Can open a command prompt by pressing, on their keyboard, the `Windows` key followed by the `R` key, which will open the `Run` dialog box, and typing:

				cmd

			and pressing `Enter`. 
    * **Note:** If Vagrant is already installed, use `vagrant -v` to check the version. You may want to consider [upgrading](http://docs.vagrantup.com/v2/installation/upgrading.html) if a much older version is in use.
4. Clone or extract the project's repository into a local directory, e.g.
    * `git clone git://github.com/vDevices/Vagrant-LinuxDesktop.git Vagrant-LinuxDesktop`
    * OR use [GitHub for Windows](http://windows.github.com/) or [GitHub for Mac](http://mac.github.com/) by clicking on the `Clone in Desktop` button;
    * OR download and extract the repository master [zip file](https://github.com/vDevices/Vagrant-LinuxDesktop/archive/master.zip)
5. Change into the new directory with `cd Vagrant-LinuxDesktop`

	#### The First `vagrant up`

6. Start the Vagrant environment by executing the command: `vagrant up`
    * Be patient as the magic happens. This could take a while on the first run as your local machine downloads the required files.

### What Did That Do?

The first time you run `vagrant up`, a packaged box  from the [Ubuntu Cloud Images](http://cloud-images.ubuntu.com/) repository, containing a basic virtual machine, is downloaded to your local computer and cached for future use. The default `Vagrantfile` used by `Vagrant's Linux Desktop Environment for Windows & Mac` contains an installation of `Ubuntu 13.10 32-bit`.

After this box is downloaded, it begins to boot as a sandboxed virtual machine using VirtualBox. Once booted, it runs the included provisioning script, to install the Ubuntu desktop environment.

The time for all of this to happen depends a lot on the speed of your Internet connection. If you are on a fast cable connection, it will likely only take several minutes.

On future runs of `vagrant up`, the packaged box will be cached on your local machine and Vagrant will only need to apply the requested provisioning.

* ***Preferred:*** If the virtual machine has been powered off with `vagrant halt`, `vagrant up` will quickly power on the machine without provisioning.
* ***Rare:*** If you would like to reapply the provisioning scripts with `vagrant up --provision` or `vagrant provision`, some time will be taken to check for updates and packages that have not been installed.
* ***Very Rare:*** If the virtual machine has been destroyed with `vagrant destroy`, it will need to download the full 100MB of package data on the next `vagrant up`.

### Now What?

Now that you're up and running, start poking around and modifying things.

1. Access the server via the command line with `vagrant ssh` from your `Vagrant-LinuxDesktop` directory. You can do almost anything you would do with a standard Ubuntu installation.
	* **Note:** Unfortunately, an SSH client is generally not distributed with Windows, by default. A terminal-emulator program such as [PuTTY](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html) will provide access immediately.
1. Destroy the box and start from scratch with `vagrant destroy`
	* As explained before, the initial 280MB box file will be cached on your machine. the next `vagrant up` command will initiate the complete provisioning process again.
1. Power off the box with `vagrant halt` and turn it back on with `vagrant up`.
1. Suspend the box's state in memory with `vagrant suspend` and bring it right back with `vagrant resume`.
1. Reapply provisioning to a running box with `vagrant provision`.

## Need Help?

* Read the Vagrant [Docs](http://docs.vagrantup.com/v2/) (while boring, that is a great place to get started).
* Open an [Issue](https://github.com/vDevices/Vagrant-LinuxDesktop/issues) on GitHub if you run into trouble or have any suggestions.

	>For more information on GitHub's Issue Tracker, consult [Issues 2.0: The Next Generation | GitHub Blog](https://github.com/blog/831-issues-2-0-the-next-generation).

* Vagrant has a [Mailing List](https://groups.google.com/forum/#!forum/vagrant-up) for any topic related to Vagrant.

## Credits

A HUGE **Thank You** is in order to:

* [Portal Stack: Vagrant + VirtualBox + Ubuntu for linux development](http://portalstack.blogspot.com/2013/11/vagrant-virtualbox-ubuntu-for-linux.html) | By [Mike Kunze](https://github.com/mikekunze?tab=repositories) (for planting the seeds for this idea); _and_
* The trailblazers at the uber-successful [Varying Vagrant Vagrants](https://github.com/10up/varying-vagrant-vagrants), which &ndash; in addition to their great work on local WordPress development &ndash; have, in the process, created a roadmap for launching _any_ local-development environment off the ground.

## Additional Resources

* [Ubuntu Cloud Images](http://cloud-images.ubuntu.com/vagrant/) (pre-installed disk images that have been customized by Ubuntu engineering to run on cloud-platforms  or in local virtualizaition environments such as Vagrant).
* [Vagrantbox.es](http://www.vagrantbox.es/) (a list of Vagrant [boxes](http://docs.vagrantup.com/v2/boxes.html) people have been nice enough to make publicly available).