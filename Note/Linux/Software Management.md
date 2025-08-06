- to use linux swiftly we need to find, download and remove tools from our system.
-  we have to download .deb package for debian based distribution dnf for fedora and pacman for arch.
### Repository
Repository in context of linux is storage location from which software packages are retrieved and installed on a system.
packages are managed using advanced package tool (apt)
these packages contains `deb` packages allowing us to install, update and manage software.

### Advanced Package Tool (APT)
is a centralized storage location containing software packages and [^1]metadata for debian based system like Ubuntu and Kali
Repository are categorized as  main, restricted, universe and multiverse depending on software licence and support.
we can access apt resources through the source list in `/etc/apt/sources.list`
and `apt-get` and  'apt ' to interact with them.
- They ensure secure, efficient software management through signed packages and regular updates.


[^1]: data providing information about one or more aspect of data

### Locating a Package
- Before downloading we can verify the package availability in the repository (a centralized database where operating system maintains software information).
- APT tool includes a search feature that allows us to determine if the desired package is accessible.
- APT uses a database called APT cache which is used to provide information about packages installed in our system offline.
``` Shell
apt-cache search packagename
apt-cache search nginx
```
`apt get-update` is used to refresh the local package index by fetching the latest information from repository.
ensures the system is aware of newest version of packages and their dependencies, but it doesnot install or upgrade any software
`apt-get upgrade` installs the latest version of all current installed packages available in the repository.
this command upgrades packages to newest version while preserving existing configuration.
together can be used to keep our system secure, up-to-date and functioning efficiently by ensuring us to have access to latest software update and security patches
`-y` can be used to confirm the process
like `sudo apt-get upgrade -y`

### Installing a software package
To install software from  operating system’s default repository via the terminal, we can use the `apt-get` command, followed by the `install` keyword and the name of the desired package.
``` Shell
sudo apt-get install  nmap -y

```
we can check installed packages by using  `--installed`
``` Shell
apt list --installed
```

### Removing software package
we can remove a package from our system by using `remove` and `purge` command
``` Shell
sudo apt-get remove <package-name>
sudo apt-get remove Obsidian #partial cleanup
sudo apt-get purge nmap #comnplete cleanup
```
### Additional package managing tools
#### Dpkg 
it is the low level package manager tool for kali or ubuntu
can be used to remove, install and manage `.deb` packages
``` Shell
sudo dpkg -i <package-name.deb> # for installing a package
sudo dpkg -r <package-name.deb> # for removing a package
sudo dpkg --purge <package_name.deb> #for removing a package including  configuring files
```
we can use apt or dpkg if we have `.deb` package

#### PIP
is it the package manager tool in python to install, manage and remove the packages .
it makes the process of adding the third party library to out python environment easier
``` Python
pip install <package_name> #to install a package
pip install django
pip uninstall <package-name> #to uninstall a package
pip list #used to list the installed packages of python

```
#### Adding repository to your `source.list` file
the server that host software for specific linux distribution are known as repositories
every Linux distribution has its own repositories
the repository contain software specifically developed and configured for that distribution.
in kali Linux, the primary repository is tailored for security and hacking tools.
repositories the system searches for software are defined in the `sources.list` file.
we can add debian or ubuntu repository after kali repository in `sources.list`
when we request a software package, the system first checks the Kali repository and if the package isn't found there then it searches the Debian or Ubuntu repository.
the location of `source.list` file is `/etc/apt/sources.list` and we can open it

