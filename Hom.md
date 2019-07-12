- - - 
**Please do not change the title of any wiki page without a permission from Tesseract developers.**
- - -

# Introduction 

Tesseract is an open source [text recognizer (OCR)](https://en.wikipedia.org/wiki/Optical_character_recognition) Engine, available under the [Apache 2.0 license.](http://www.apache.org/licenses/LICENSE-2.0) It can be used directly, or (for programmers) using an [API](https://github.com/tesseract-ocr/tesseract/blob/master/src/api/baseapi.h) to extract printed text from images. It supports a wide variety of languages.

Tesseract doesn't have a built-in GUI, but there are several available from the [3rdParty](https://github.com/tesseract-ocr/tesseract/wiki/User-Projects-%E2%80%93-3rdParty) page.

# Installation

There are two parts to install, the engine itself, and the training data for a language.

## Linux

Tesseract is available directly from many Linux distributions. The package is generally called **'tesseract'** or **'tesseract-ocr'** - search your distribution's repositories to find it.
Thus you can install Tesseract 4.x and it's developer tools on Ubuntu 18.x bionic by simply running:
```
sudo apt install tesseract-ocr
sudo apt install libtesseract-dev
```

**Note for Ubuntu users**: In case ```apt``` is unable to find the package try adding ```universe``` entry to the ```sources.list``` file as shown below. 
```
sudo vi /etc/apt/sources.list

Copy the first line "deb http://archive.ubuntu.com/ubuntu bionic main" and paste it as shown below on the next line.
If you are using a different release of ubuntu, then replace bionic with the respective release name.

deb http://archive.ubuntu.com/ubuntu bionic universe
```


Packages for over 130 languages and over 35 scripts are also available directly from the Linux distributions. The language packages are called **'tesseract-ocr-langcode'** and **'tesseract-ocr-script-scriptcode'**, where langcode is three letter language code and scriptcode is four letter script code. 

**Examples:** tesseract-ocr-eng (**English**), tesseract-ocr-ara (**Arabic**), tesseract-ocr-chi-sim (**Simplified Chinese**), tesseract-ocr-script-latn (**Latin Script**),  tesseract-ocr-script-deva (**Devanagari script**), etc.

For distributions that are supported by snapd you may also run the following command to install the `tesseract` built binaries([Don't have snapd installed?](https://snapcraft.io/docs/core/install)):

    sudo snap install --channel=edge tesseract

The traineddata is currently not shipped with the snap package and must be placed manually to `~/snap/tesseract/current`.

### Tesseract 4 packages with LSTM engine and related traineddata.

#### Debian

* [Debian Jessie (notesalexp.org)](https://notesalexp.org/tesseract-ocr/)
* [Debian Stretch (backports)](https://packages.debian.org/stretch-backports/tesseract-ocr)
* [Debian Buster (testing)](https://packages.debian.org/buster/tesseract-ocr)
* [Debian Sid (unstable)](https://packages.debian.org/sid/tesseract-ocr)

#### Ubuntu

* [Ubuntu Bionic 18.04](https://packages.ubuntu.com/bionic/tesseract-ocr-all) 
* [Ubuntu Cosmic 18.10](https://packages.ubuntu.com/cosmic/tesseract-ocr-all) 

#### Ubuntu - PPA / packages from notesalexp.org 
* [Ubuntu Bionic 18.04 - PPA ](https://launchpad.net/~alex-p/+archive/ubuntu/tesseract-ocr?field.series_filter=bionic)
* [Ubuntu Artful 17.10 - PPA](https://launchpad.net/~alex-p/+archive/ubuntu/tesseract-ocr?field.series_filter=artful)
* [Ubuntu Zesty 17.04 - notesalexp.org](https://notesalexp.org/tesseract-ocr/)
* [Ubuntu Xenial 16.04 - PPA](https://launchpad.net/~alex-p/+archive/ubuntu/tesseract-ocr?field.series_filter=xenial)
* [Ubuntu Trusty 14.04 - PPA](https://launchpad.net/~alex-p/+archive/ubuntu/tesseract-ocr?field.series_filter=trusty)

#### Raspbian
* [Raspbian Stretch(notesalexp.org)](https://notesalexp.org/tesseract-ocr/)
* [Raspbian Buster (testing)](http://raspbian.org/RaspbianRepository)

#### CentOS, Fedora, ScientificLinux, OpenSuse, RHEL packages

* [rpm package with tesseract-ocr](https://build.opensuse.org/project/show/home:Alexander_Pozdnyakov)

For example to install Tesseract with German language traineddata:

**For RHEL 7 run the following as root:**

```
yum-config-manager --add-repo https://download.opensuse.org/repositories/home:/Alexander_Pozdnyakov/RHEL_7/
yum update
yum install tesseract 
yum install tesseract-langpack-deu
```

**For CentOS 7 run the following as root:**
```
yum-config-manager --add-repo https://download.opensuse.org/repositories/home:/Alexander_Pozdnyakov/CentOS_7/
sudo rpm --import https://build.opensuse.org/projects/home:Alexander_Pozdnyakov/public_key
yum update
yum install tesseract 
yum install tesseract-langpack-deu
```
**For Scientific Linux 7 run the following as root:**
```
yum-config-manager --add-repo https://download.opensuse.org/repositories/home:/Alexander_Pozdnyakov/ScientificLinux_7/
yum update
yum install tesseract 
yum install tesseract-langpack-deu
```
**For Fedora 27 run the following as root:**
```
dnf config-manager --add-repo https://download.opensuse.org/repositories/home:Alexander_Pozdnyakov/Fedora_27/home:Alexander_Pozdnyakov.repo
dnf install tesseract
dnf install tesseract-langpack-deu
```
**For Fedora 26 run the following as root:**
```
dnf config-manager --add-repo https://download.opensuse.org/repositories/home:Alexander_Pozdnyakov/Fedora_26/home:Alexander_Pozdnyakov.repo
dnf install tesseract
dnf install tesseract-langpack-deu
```
**For Fedora 25 run the following as root:**
```
dnf config-manager --add-repo https://download.opensuse.org/repositories/home:Alexander_Pozdnyakov/Fedora_25/home:Alexander_Pozdnyakov.repo
dnf install tesseract
dnf install tesseract-langpack-deu
```
**For openSUSE Tumbleweed run the following as root:**
```
zypper addrepo https://download.opensuse.org/repositories/home:Alexander_Pozdnyakov/openSUSE_Tumbleweed/home:Alexander_Pozdnyakov.repo
zypper refresh
zypper install tesseract-ocr
zypper install tesseract-ocr-traineddata-german
```
**For openSUSE Leap 42.3 run the following as root:**
```
zypper addrepo https://download.opensuse.org/repositories/home:Alexander_Pozdnyakov/openSUSE_Leap_42.3/home:Alexander_Pozdnyakov.repo
zypper refresh
zypper install tesseract-ocr
zypper install tesseract-ocr-traineddata-german
```
**For openSUSE Leap 15.0 run the following as root:**
```
zypper addrepo https://download.opensuse.org/repositories/home:Alexander_Pozdnyakov/openSUSE_Leap_15.0/home:Alexander_Pozdnyakov.repo
zypper refresh
zypper install tesseract-ocr
zypper install tesseract-ocr-traineddata-german
```

### FOR EXPERTS ONLY. 

If you are experimenting with OCR Engine modes, you will need to manually install language training data beyond what is available in your Linux distribution. 

Various types of training data can be found on [GitHub](https://github.com/tesseract-ocr/). Unpack and copy the .traineddata file into a 'tessdata' directory. The exact directory will depend both on the type of training data, and your Linux distribution. Possibilities are `/usr/share/tesseract-ocr/tessdata` or `/usr/share/tessdata` or `/usr/share/tesseract-ocr/4.00/tessdata`. 

Training data for obsolete Tesseract versions [=< 3.02](https://sourceforge.net/projects/tesseract-ocr-alt/files/?source=navbar) reside in another location.

If Tesseract is not available for your distribution, or you want to use a newer version than they offer, you can [compile your own](Compiling).

## macOS

You can install Tesseract using either [MacPorts](https://www.macports.org/) or [Homebrew](http://brew.sh).

A macOS wrapper for the Tesseract API is also available at [Tesseract macOS](https://github.com/scott0123/Tesseract-macOS).

### MacPorts
To install Tesseract run this command: 
```
sudo port install tesseract
```
To install any language data, run:
```
sudo port install tesseract-<langcode>
```
List of available langcodes can be found on [MacPorts tesseract page](https://www.macports.org/ports.php?by=name&substr=tesseract-).

### Homebrew
To install Tesseract run this command:
```
brew install tesseract
```

Training directories can be found using `brew list tesseract`
Possible location can be `/usr/local/Cellar/tesseract/3.05.02/share/tessdata/`

## Windows

Installer for Windows for Tesseract 3.05 and Tesseract 4 are available from [Tesseract at UB Mannheim](https://github.com/UB-Mannheim/tesseract/wiki). These include the training tools. Both 32-bit and 64-bit installers are available.

An installer for the **OLD version 3.02** is available for Windows from our [download](Downloads) page. This includes the English training data. If you want to use another language, [download the appropriate training data](
https://github.com/tesseract-ocr/tesseract/wiki/Data-Files), unpack it using [7-zip](http://www.7-zip.org), and copy the .traineddata file into the 'tessdata' directory, probably `C:\Program Files\Tesseract-OCR\tessdata`.

To access tesseract-OCR from any location you may have to add the directory where the tesseract-OCR binaries are located to the Path variables, probably `C:\Program Files\Tesseract-OCR`.

Experts can also get binaries build with Visual Studio from the build artifacts of the [Appveyor Continuous Integration](https://ci.appveyor.com/project/zdenop/tesseract/history).

### Cygwin

Released version >= 3.02 of tesseract-ocr [are part of ](https://mirrors.kernel.org/sourceware/cygwin/x86_64/release/tesseract-ocr/) [Cygwin](https://www.cygwin.com/)

The latest version available is 4.00. Please see [announcement](https://www.cygwin.com/ml/cygwin-announce/2018-10/msg00020.html).

### MSYS2

Install tesseract-OCR:

```
 pacman -S mingw-w64-{i686,x86_64}-tesseract-ocr
```

and the data files:

```
 pacman -S mingw-w64-{i686,x86_64}-tesseract-data-eng
```

In the above command, "eng" may be replaced with the [ISO 639 3-letter language code](http://www.loc.gov/standards/iso639-2/php/code_list.php) for supported languages. For a list of available language packages use:

```
  pacman -Ss tesseract-data
```

## Other Platforms

Tesseract may work on more exotic platforms too. You can either try [compiling it yourself](Compiling), or take a look at the list of [other projects using Tesseract](https://github.com/tesseract-ocr/tesseract/wiki/User-Projects-%E2%80%93-3rdParty).


# Running Tesseract

Tesseract is a command-line program, so first open a terminal or command prompt. The command is used like this:

```
  tesseract imagename outputbase [-l lang] [-psm pagesegmode] [configfile...]
```

So basic usage to do OCR on an image called 'myscan.png' and save the result to 'out.txt' would be:

```
  tesseract myscan.png out
```

Or to do the same with German:

```
  tesseract myscan.png out -l deu
```

It can even be used with multiple languages traineddata at a time eg. English and German:

```
  tesseract myscan.png out -l eng+deu
```

Tesseract also includes a hOCR mode, which produces a special HTML file with the coordinates of each word. This can be used to create a searchable pdf, using a tool such as [Hocr2PDF](https://exactcode.com/opensource/exactimage/). To use it, use the 'hocr' config option, like this:

```
  tesseract myscan.png out hocr
```

You can also create a searchable pdf directly from tesseract ( versions >=3.03):

```
  tesseract myscan.png out pdf
```

More information about the various options is available in the [Tesseract manpage](https://github.com/tesseract-ocr/tesseract/blob/master/doc/tesseract.1.asc).

# Other Languages

Tesseract has been trained for [many languages](https://github.com/tesseract-ocr/tesseract/blob/master/doc/tesseract.1.asc#languages), check for your language in the [Tessdata repository](https://github.com/tesseract-ocr/tessdata). 

It can also be trained to support other languages and scripts; for more details see [TrainingTesseract](TrainingTesseract).

# Development

Tesseract can also be used in your own project, under the terms of the [Apache License 2.0.](http://www.apache.org/licenses/LICENSE-2.0) It has a fully featured API, and can be compiled for a variety of targets including Android and the iPhone. See the [3rdParty](https://github.com/tesseract-ocr/tesseract/wiki/User-Projects-%E2%80%93-3rdParty) page for a sample of what has been done with it. Note that as yet there are very few  3rdParty Tesseract OCR projects [being developed for Mac](https://machow2.com/ocr-for-mac-best-software/#Tesseract_Freesoftware/) (with the only one being [Tesseract macOS](https://github.com/scott0123/Tesseract-macOS)), although there are several online OCR services that can be used on Mac that may use Tesseract as their OCR engine. 

Also, it's free software, so if you want to pitch in and help, please do!
If you find a bug and fix it yourself, the best thing to do is to attach the patch to your bug report in the [Issues List](https://github.com/tesseract-ocr/tesseract/issues)

# Support

First read the [Wiki](https://github.com/tesseract-ocr/tesseract/wiki), particularly the [FAQ](FAQ) to see if your problem is addressed there. If not, search the [Tesseract user forum](http://groups.google.com/group/tesseract-ocr) or the [Tesseract developer forum](http://groups.google.com/group/tesseract-dev), and if you still can't find what you need, please ask us there.