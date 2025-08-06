
### step 1: Download the .deb package

.deb is for debian linux
### step2: go to root directory

root directry allows to change the system components

```bash
sudo su 
```

sudo=superuser do

su=switch user

```bash
apt update
```

to update package list of internet

apt=advanced package tool

```bash
cd Downloads
ls
```

this changes the directory to downloads i.e. change the directory to the location of package

ls is used to list files and folder of the directory

### step 3: Make executable file

```bash
chmod +x <filename/packagename>
```

chmod=change mode

+x=add execute permission

### step 5: Install the package

```bash
dpkg -i <packagename.deb>

```

dpkg=debian package manager

-i=install