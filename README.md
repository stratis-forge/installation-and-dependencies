## Installing dependencies for STRATIS workflows

STRATIS workflows use various image processing libraries for data transformation, registration and segmentation. The workflows are provided in the form of Jupyter notebooks. Python packages and related dependencies are installed within an Anaconda environment as described in a section on this page. The workflows that use [CERR](https://www.github.com/cerr) for feature extraction and image segmentaition require GNU Octave to be installed on the host computer. 

### Pre-requisites for installing GNU Octave
* On Windows, MinGW or .NET is required to use Octave. MinGW can be installed from https://www.mingw-w64.org/downloads/#mingw-builds. 
* GNU Octave uses Qt for graphics. Install Qt at https://www.qt.io/download-qt-installer


### GNU Octave Installation

* Windows and Mac: follow instructions at https://octave.org/download. 
* Linux: Our group has pre-compiled Octave with Java. Follow the installation instructions below.

```
apt-get update
apt-get -y install curl wget nano libgraphicsmagick++1-dev libsuitesparse-dev libqrupdate1 libreadline7 libfftw3-3 libhdf5-100 libgl1 libglu1-mesa libgl2ps1.4 \
        libcurl4-gnutls-dev libarpack2 libopenblas-base git gnuplot libqt5gui5 libqt5core5a

mkdir /content

LOCATION=$(curl -s https://api.github.com/repos/cerr/octave-colab/releases/latest \
| awk -F\" '/browser_download_url/ { print $4 }') && curl -L -o /content/octavecolab.tar.gz $LOCATION
 
cd /content && tar xzvf /content/octavecolab.tar.gz
chmod -R 777 /content

export OCTAVE_EXECUTABLE=/content/octave/bin/octave-cli
```

* Add `JAVA_HOME` and `OCTAVE_EXECUTABLE` environment variables to point to the respective Java Runtime and GNU Octave locations. For eample, `JAVA_HOME` might be located at `C:\Program Files (x86)\Java\jre1.8.0_351`and `OCTAVE_EXECUTABLE` at `C:\Program Files\GNU Octave\Octave-7.3.0\mingw64\bin\octave-gui.exe`
* Open Octave and install additional packages at the command line:
```
pkg install -forge io;
pkg install -forge statistics; 
pkg install -forge image;
```

### CERR Installation
CERR can be downloaded from GitHub to a desired location as follows.
```
cd C:/software/cerr
git clone --single-branch --branch octave_dev https://www.github.com/cerr/CERR.git
```

## Creating Conda environment for STRATIS 

Step1: Install Miniconda following the instructions at https://docs.conda.io/en/latest/miniconda.html

Step 2: Download requirements file for your OS from https://github.com/stratis-forge/installation-and-dependencies. Note that the requirements file can be extended as needed by the user to use additional packages.

Step 3: Build conda environment 

Issue the following command from Miniconda prompt:
```
conda env create -f C:/software/stratis-forge/installation-and-dependencies\requirements_win.txt \
   -p C:\Users\username\Miniconda3\envs\stratis
```

Step 4: Activate the newly created environment

Issue the following command from Miniconda prompt:
```
conda activate C:\Users\username\Miniconda3\envs\stratis
```

Step 5: Start Jupyter lab server.

Issue the following command from Miniconda prompt:
```
jupyter lab
```

Step 6: To deactivate/activate the current environment

Issue the following command from Miniconda prompt:
```
conda deactivate
```
