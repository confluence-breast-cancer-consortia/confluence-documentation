# dx-toolkit

The dx-toolkit provides command-line tools for working with DNANexus Platform, and they are very useful, so it is worthwhile to spend some time to read up on the [documentation](https://documentation.dnanexus.com/user/helpstrings-of-sdk-command-line-utilities).&#x20;

### Installation

DNANexus provides instructions on how to install it using pip3 [here](https://documentation.dnanexus.com/downloads). However I prefer following the [St. Jude Cloud docs](https://university.stjude.cloud/docs/genomics-platform/analyzing-data/creating-a-cloud-app/) to install it in its own conda environment. Briefly, if you have conda/miniconda installed at your local computer, create a dx conda environment and pip install dxpy:

```
conda create -n dx python=3.7
conda activate dx
pip install dxpy
```

### Usage

The dx-toolkit is a convenient way to interact with the DNANexus cloud platform and can almost feel like working on a HPC cluster with commands prefixed with 'dx'. It can be utilized for various ways:

1. Data Management: For example, using the `dx upload` and `dx download` command-line tools to transfer files, as well as  using the `dx describe` and `dx set_properties` commands to manage metadata associated with the files.
2. Workflow Execution: We can use  the `dx find apps` and `dx run` commands to find and run apps from the DNAnexus app store,  using the `dx new workflow` command to create a new workflow with custom apps, using the `dx wait` and `dx watch` commands to monitor the progress of the workflow execution.&#x20;
3. Custom App Development: using the `dx build` and `dx add app` commands to build DNANexus Apps (more on this in the later chapters)



