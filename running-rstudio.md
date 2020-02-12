# Running RStudio

## Starting Sid

In all cases you need to start Sid

* In the browser go to [https://sid.hmdc.harvard.edu](https://sid.hmdc.harvard.edu)
* Launch Sid
* Click `Run An Interactive Application`

## Running RStudio

* Select RStudio
* Select Version
* Click Google drive \(login if necessary\)
* Select CPU/RAM
* Click `Launch Application`
* Wait until URL is visible. The status will change from `Initializing` to `Running`
* Click on the URL

You can now create a RStudio Project.


{% hint style="warning" %}
Your RStudio home directory is on ephemeral storage. This means that when the container is deleted all the files will be lost. Store your files on Google Drive to save your work.
{% endhint %}

## Accessing Google Drive

If you want to access google drive you need to to a couple of steps:

* Choose the **Terminal** tab
* Run the following command:

```bash
ln -s /mnt/google-drive $HOME
```

* In the File Browser pane, google-drive is now available

## Installing and Using R Libraries

Using R libraries in RStudio is easy. Run the `library` command in the **Console** tab:

```r
library(tidyverse) 
library(gridExtra)
```

If a library is not available and get an error like this. In this case the \`dslabs\` library is missing:

```text
Error in library(dslabs): there is no package called ‘dslabs’
```

Install the package from within your notebook with:

```r
install.packages("dslabs")
```

## Installing System Libraries

Some R libraries require additional system libraries. If the required system libraries are not installed, `install.packages()` will report an error like this:

```text
------------------------- ANTICONF ERROR ---------------------------
Configuration failed because libxml-2.0 was not found. Try installing:
 * deb: libxml2-dev (Debian, Ubuntu, etc)
 * rpm: libxml2-devel (Fedora, CentOS, RHEL)
 * csw: libxml2_dev (Solaris)
If libxml-2.0 is already installed, check that 'pkg-config' is in your
PATH and PKG_CONFIG_PATH contains a libxml-2.0.pc file. If pkg-config
is unavailable you can set INCLUDE_DIR and LIB_DIR manually via:
R CMD INSTALL --configure-vars='INCLUDE_DIR=... LIB_DIR=...'
--------------------------------------------------------------------
```

To install additional system libraries, use the R function `system()` to run `sudo apt-get update` and `sudo apt-get install` to install the **Debian** packages:

```r
system("sudo apt-get update")
system("sudo apt-get install -y libxml2-dev")
```
