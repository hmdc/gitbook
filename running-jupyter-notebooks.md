# Running Jupyter notebooks

## Starting Sid

In all cases you need to start Sid

* In the browser go to [https://sid.hmdc.harvard.edu](https://sid.hmdc.harvard.edu)
* Launch Sid
* Click `Run An Interactive Application`

## Running Jupyter

The basic steps for Python, R or Julia notebooks are the same:

* Select Jupyter
* Select Version
* Click Google drive \(login if necessary\)
* Select CPU/RAM
* Click `Launch Application`
* Wait until URL is visible. The status will change from `Initializing` to `Running`.
* Click on the URL

You can now create a Jupyter notebook.

Click on the `New` button on the top right and select Julia, Python or R.

**Video tutorial of these steps:**

[![Starting a Jupyter Notebook](.gitbook/assets/Starting%20a%20Jupyter%20Notebook.png)](https://drive.google.com/open?id=1-jW7whc5wOtHN4GM159VyXG4_-NsP4ZD)

{% hint style="warning" %}
At this moment you notebooks are saves on ephemeral storage. This means that when the container is deleted all the files will be lost. Store your files on Google Drive to save your work.
{% endhint %}

## Accessing Google Drive

If you selected Google Drive as your storage provider when running a Jupyter notebook on Sid, the ```google-drive``` folder will be available in the default location as a subfolder of Jupyter's home directory. You should see the ```google-drive``` immediately upon accessing your job via the Sid-produced job url.

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

**Video tutorial of these steps:**

[![Installing Python Modules in Jupyter](.gitbook/assets/Installing%20python%20modules%20in%20Jupyter.png)](https://drive.google.com/open?id=1S6STWYTd3r5J8wjPZOgDR0VOHLB9JSAA)

## Creating a script for installing Python libraries

Just as files on the ephemeral storage will be lost after deleting the container, so will the libraries need to be reinstalled for every container. To make things easier you can write a file that you can run to install the libraries you need.

{% hint style="info" %}
This is a different way than explained in the video tutorial. Working with `requirements.txt` is a more standard way of doing this.
{% endhint %}

### Creating the script

* Choose `New>Text File`
* In text file write the names of the libraries you want to install. Write one library on each line.

```text
lxml
```

* Choose `File>Save` and save the file as: `requirements.txt.`
* Make sure it is saved on Google Drive
* Close the Tab

### Running the script

* Open a terminal from Jupyter: `New > Terminal`
* `cd` into the directory where you saved the file
* run the command the following command to install all the libraries:

```text
pip install -r requirements.txt
```

**Video tutorial of these steps:**

[![Create an install Script for Python modules in Jupyter](.gitbook/assets/Create%20an%20install%20script.png)](https://drive.google.com/open?id=1RzqCegn7-QI9Swb3PEfmc0dWceQfAqOm)

## Using and installing R Libraries

Installing R libraries in Jupyter is easy. Using libraries you add the library command in the notebook cells:

```r
library(tidyverse) 
library(gridExtra)
```

If a library is not available and get an error like this. In this case the \`dslabs\` library is missing:

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

