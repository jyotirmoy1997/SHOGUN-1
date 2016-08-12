Shallow shotgun sequencing
=======
Shallow seq pipeline for optimal shotgun data usage

## Installation
These installation instructions are streamlined for Linux and OSX devices. The tool SHOGUN is installable on windows with a few minor tweaks to this tutorial. This package requires anaconda, which is a system agnostic package and virtual environment manager. Follow the installation instructions for your system at <http://conda.pydata.org/miniconda.html>.

Once anaconda is installed, create a new virtual environment with python3.

```
conda create -n shogun python=3
```

Now activate the environment.

```
# OSX, Linux
source activate shogun
```

With the shogun environment activated, install the developmental SHOGUN toolchain.

```
# bowtie2
conda install -c bioconda bowtie2

# NINJA-utils
pip install git+https://github.com/knights-lab/NINJA-utils.git --no-cache-dir --upgrade

# NINJA-DOJO
pip install git+https://github.com/knights-lab/NINJA-DOJO.git --no-cache-dir --upgrade

# NINJA-SHOGUN
pip install git+https://github.com/knights-lab/NINJA-SHOGUN.git --no-cache-dir --upgrade
```

All dependencies should now be installed for NINJA-SHOGUN. If anything fails, try to directly conda install the failed package as the conda package manager is more robust to errors than pip. For example, if scipy failed.

```
conda install scipy
```

With the flags provided to pip, copying and pasting any of these commands will redo the installation if a failure happened. Next, to test the installation, download the test data.

```
wget https://www.dropbox.com/s/b5w4xe08x7snm93/shogun_test_files.zip?dl=1
```

Extract the folder using your favorite extraction utility.

```
7z x <downloaded file>
```

Next you create the database.

```
shogun_bt2_db -i ./test.hmp_species.fna -x '>, '
```

This will take some time, the DOJO software is lazy loading the NCBI Taxonomy.

```
cd mock_communities
shogun_bt2_lca -i ./ -b ../annotated/bt2/test.hmp_species
```

The results of the taxonomy counts will be in the taxon_counts.csv 🐱‍👤

