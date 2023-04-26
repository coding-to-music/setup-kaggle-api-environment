# ev-charging-stations-kaggle

# 🚀 Download via Kaggle API the EV Charging Stations dataset 🚀

https://github.com/coding-to-music/ev-charging-stations-kaggle


From / By 
## Environment variables:

```java
kaggle.json is needed, see below
```

## GitHub

```java
git init
git add .
git remote remove origin
git commit -m "first commit"
git branch -M main
git remote add origin git@github.com:coding-to-music/ev-charging-stations-kaggle.git
git push -u origin main
```

# how to download via Kaggle API the dataset

```
# Make directory named kaggle, copy kaggle.json file there, and change the permissions of the file.
! mkdir ~/.kaggle
! cp kaggle.json ~/.kaggle/
! chmod 600 ~/.kaggle/kaggle.json

# You can check if everything's okay by running this command.
! kaggle datasets list

# Download and unzip sign-language-mnist dataset into '/usr/local'
! kaggle datasets download -d datamunge/sign-language-mnist --path '/usr/local' --unzip
```

## Another way

```
import os

os.environ['KAGGLE_USERNAME'] = "xxxx"

os.environ['KAGGLE_KEY'] = "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"

!kaggle datasets download -d iarunava/happy-house-dataset
```

# Third way, as for Google Colab

1. Read the kaggle API token to interact with your kaggle account

```
from google.colab import files
files.upload()
```

2. Series of commands to set-up for download

```
!ls -lha kaggle.json
!pip install -q kaggle # installing the kaggle package
!mkdir -p ~/.kaggle # creating .kaggle folder where the key should be placed
!cp kaggle.json ~/.kaggle/ # move the key to the folder
!pwd # checking the present working directory
```

3. giving rw access (if 401-nathorized)

```
!chmod 600 ~/.kaggle/kaggle.json
Else retry with fresh API token
```

4. Sanity check if able to access kaggle

```
!kaggle datasets list
```

5. Download data command

```
!kaggle datasets download -d insert_dataset_suffix_ -p location_where_to_download
for example: !kaggle datasets download -d thedevastator/hubmap-2022-512x512 -p </content/drive/MyDrive/Task2_hubmap
```

6. unzip

```
!unzip */content/drive/MyDrive/Task2_hubmap/hubmap-2022-512x512.zip *-d /content/drive/MyDrive/Task2_hubmap/hubmap-2022-512x512/
```

# Easily Obtain Kaggle Datasets In Python

https://medium.com/geekculture/easily-obtain-kaggle-datasets-in-python-d15a5ede313d

Kaggle is an excellent platform for data science and machine learning practitioners. Be it for learning, joining competitions, or exploring datasets, its public API offers an option to obtain datasets easily.

As such, this post will be looking at how to install, set up and access the API to obtain Kaggle datasets.

## Installation

To install kaggle on your base / virtual environment, run the following pip install.

```
pip install kaggle
```

## Obtaining Authentication

After installing the package, we would require credentials to access its public API. So, firstly, create a Kaggle account if you haven’t already. Next, click on the top right-hand corner to access your profile and click on the Account tab.

From which, scroll down a little until you see the API section. Click on “Create New API Token” to download your credentials. It would be in a JSON format file consisting of your username and key.


## Moving Credentials To Folder

The next step before using the API endpoints would be to store your credentials in the correct folder.

By default, after the pip installation, a new folder would be created with the following path: C:\Users\<Windows-username>\.kaggle

Move the JSON file to the Kaggle path created via installation.

## Exploring Kaggle API Endpoints

After following the steps above, we can begin exploring the use of this package. I would be executing them in a Jupyter Notebook.

The Kaggle API offers the following endpoints with various commands:

```
Competitions {list, files, download, submit, submissions, leaderboard}
Datasets {list, files, download, create, version, init}
Kernels {list, init, push, pull, output, status}
Config {view, set, unset}
Competitions Endpoint
```

Suppose we would like to access the datasets of currently active competitions on Kaggle; we can do so with the following command.

```
!kaggle competitions list
```

Using the other commands, we can also check out the leaderboard scoring for a competition. For example, suppose we are interested to see the leaderboard for the “contradictory-my-dear-watson” competition.

```
!kaggle competitions leaderboard --show contradictory-my-dear-watson
```

We can also search for competitions with a keyword. For example, suppose we want to search for competitions related to finance.

```
!kaggle competitions list -s finance
```

To check the files associated with a competition dataset, we can use the following command.

```
!kaggle competitions files titanic
```

To explore more endpoints, use the following command.

```
!kaggle competitions -h
```

Datasets Endpoint

Similar to the competitions endpoints, we can also obtain datasets using the datasets endpoint. Thus, we would replace the competition with datasets.

```
!kaggle datasets list
```

We can also sort the datasets by most active and last updated.

```
!kaggle datasets list --sort-by active
```

To explore more endpoints, use the following command.

```
!kaggle datasets -h
```

Downloading, Unzipping and Reading Kaggle Datasets

Finally, we can also download the files associated with a competition or dataset. For example, suppose I am interested in downloading the files for “Reddit Vaccine Myth”.

Firstly, obtain the reference of the dataset. For Reddit Vaccine Myth, we can see that the reference for the dataset is: `gpreda/reddit-vaccine-myths`

```
!kaggle datasets list
```

Once we have the dataset’s reference, we can download the files using the following command.

```
!kaggle datasets download gpreda/reddit-vaccine-myths
```

By default, the files would be downloaded into your current working Python script directory in a ZIP file.

To extract a ZIP file, use the following function.

```
from zipfile import ZipFile
  
with ZipFile('reddit-vaccine-myths.zip', 'r') as zip:
    zip.printdir()
    zip.extractall()
```

Once that’s done, read in your files!

```
import pandas as pd
df = pd.read_csv("reddit_vm.csv")
df.head()
```

Simple as that! Once set up, this would likely help streamline the model building processing by obtaining and reading data directly from Kaggle.

The complete documentation can be found: Kaggle.https://github.com/Kaggle/kaggle-api

