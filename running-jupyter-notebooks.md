# Running Jupyter notebooks

## Starting Sid

In all cases you need to start Sid

* Goto [https://sid.hmdc.harvard.edu](https://sid.hmdc.harvard.edu)
* Launch Sid
* Click `Run An Interactive Application`

## Running Jupyter

The basic steps for Python, R or Julia notebooks are the same:

* Select Jupyter
* Select Version
* Click Google drive \(login if neccesary\)
* Select CPU/RAM
* Click `Launch Application`
* Wait until URL is visible. The status will change from `Initializing to` \`Running\`\)
* Click on the URL

You can now create a Jupyiter notebook. 

Click on the  `New` button on th top right and select Julia, Python or R. 

{% hint style="warning" %}
At this moment you notebooks are saves on ephemeral storage. This means that when the container is deleted all the files will be lost. Store your files on Google Drive to save your work.
{% endhint %}

## Accessing Google Drive

If you want to access google drive you need to to a couple of steps:

* Choose `New>Terminal`
* Run the following commands:

```bash
rm -r /home/jovyan/work
ln -s /mnt/google-drive /home/jovyan/google-drive
```

* Close the tab with the Terminal
* In the overview google-drive is now available

## Installing Python libraries

Some libraries are already installed in the Python notebooks of Jupyter. `ggplot2` or `pandas` for example. Other libraries will need to be installed manually.

* Open a new terminal `New>Terminal`
* run this to install libraries

```text
pip install <library name>
```

For example if`lxml` is not installed, you will get an error like this.

```text
ModuleNotFoundError                      Traceback (most recent call last)
<ipython-input-2-72d693772b13> in <module>
----> 1 from lxml import html
      2 
      3 events_html = html.fromstring(events0.text)

ModuleNotFoundError: No module named 'lxml'

```

In this case you need to install lxml using:

```text
pip install lxml
```

## Creating a script for installing Python libraries

Just as files on the ephemeral storage will be lost after deleting the container, so will the libraries need to be reinstalled for every container. To make things easier you can write a file that you can run to install the libraries you need.

### Creating the script

* Choose `New>Text File`
* Write the script with all the lines needed for the installation

```text
pip install lxml
# Add more lines if needed
# pip install ....
```

* Choose `File>Save` and save the file, for example as: `install_libraries.txt.`
* Make sure it is saved on Google Drive
* Close the Tab

### Running the script

* Open a terminal from Jupyter: `New > Terminal`
* `cd` into the directory where you saved the file
* run the command:

```text
bash ./install_libraries.txt
```

{% hint style="info" %}
Setting file permissions is not possible in the Terminal for Google Drive \(`chmod` will not work\). Therefore we are running the script using the `bash` command and do not include `#!/bin/bash` in the script file
{% endhint %}

## Using and installing R Libraries

Installing R libraries in Jupyter is easy. Using libraries you add the library command in the notebook cells:

```r
library(tidyverse) 
library(gridExtra)
```

If a library is not available and get an error like this. In this case the \`dslabs\`  library is missing:

```text
Error in library(dslabs): there is no package called ‘dslabs’
Traceback:

1. library(dslabs)
2. stop(txt, domain = NA)
```

Install the package from within your notebook with:

```r
install.packages("dslabs")
```

