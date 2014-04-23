# Win US Intl Compose for Linux

Latin speakers (spanish, brazilian-portuguese) using a US International keyboard layout faces a different behavior from Windows(TM) to Linux.

This repo was created to try to provide the same Windows(TM) behavior for latin speakers using a `en_US` keyboard layout.

It relies on use of [`uim`](http://en.wikipedia.org/wiki/Uim) as Input Method, which supports both GTK+ and Qt immodules with legacy [`XIM`](http://en.wikipedia.org/wiki/Xim) support.


## Install Instructions

### Fedora 20

Open a terminal and run at home folder:

```term
wget https://raw.githubusercontent.com/raelgc/win_us_intl/master/.XCompose
gsettings set org.gnome.settings-daemon.plugins.keyboard active false
sudo yum -y install uim uim-gtk3
imsettings-switch -q uim
```
Logout and login (or restart all programs you were using)

### openSUSE

Open a terminal and run at home folder:

```term
wget https://raw.githubusercontent.com/raelgc/win_us_intl/master/.XCompose
sudo zypper in uim
```
Logout and login (or restart all programs you were using)

### Ubuntu

Open a terminal and run at home folder:

```term
wget https://raw.githubusercontent.com/raelgc/win_us_intl/master/.XCompose
sudo apt-get -y install uim
im-config -n uim
```
## Test

To test it, run in terminal:

`$ strace -e open xterm |& grep Compose`
    
Output will be like:

```term    
open("/home/rael/.XCompose", O_RDONLY)  = 6
open("/home/rael/.XCompose", O_RDONLY)  = 6
open("/usr/share/X11/locale/en_US.UTF-8/Compose", O_RDONLY) = 7
```
    
For Fedora 20, no output will be generated.


## Known Issues

1. Ubuntu Unity Dash don't respect the cedilla. Any other programs will work fine (Firefox, Google Chrome, Gnome programs, KDE programs, etc).
2. Some obscure key combinations haven't been covered yet (acute + ß).
3. Some dead key combinations don't work at all (acute + diaeresis != '")


## How to Contribute

If you modify this file to improve the compatibility with the
 original Windows US Intl Behavior, please open an issue in this repo.
 We'll gladly merge both files after determine those changes will
 match the usual behavior in Windows, giving credit where due
