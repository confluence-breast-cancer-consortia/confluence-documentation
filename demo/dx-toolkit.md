# dx-toolkit

The dx-toolkit provides command-line tools for working with DNANexus Platform, and they are very useful, so it is worthwhile to spend some time to read up on the [documentation](https://documentation.dnanexus.com/user/helpstrings-of-sdk-command-line-utilities).&#x20;

### Installation

DNANexus provides instructions on how to install it using pip3 [here](https://documentation.dnanexus.com/downloads). However I prefer following the [St. Jude Cloud docs](https://university.stjude.cloud/docs/genomics-platform/analyzing-data/creating-a-cloud-app/) to install it in its own conda environment. Briefly, if you have conda/miniconda installed at your local computer, create a dx conda environment and pip install dxpy:

```
conda create -n dx python=3.7
conda activate dx
pip install dxpy
```



