# dx-toolkit

The dx-toolkit provides command-line tools for working with DNANexus Platform, and they are very useful, so it is worthwhile to spend some time to read up on the [documentation](https://documentation.dnanexus.com/user/helpstrings-of-sdk-command-line-utilities).&#x20;

### Installation

DNANexus provides instructions on how to install it using pip3 [here](https://documentation.dnanexus.com/downloads). However I prefer following the [St. Jude Cloud docs](https://university.stjude.cloud/docs/genomics-platform/analyzing-data/creating-a-cloud-app/) to install it in its own conda environment. Briefly, if you have conda/miniconda installed at your local computer, create a dx conda environment and pip install dxpy:

```
conda create -n dx python=3.7
conda activate dx
pip install dxpy
```

### Interactive CLI Analysis

The dx-toolkit sometimes have conflicts with the organizational VPN. Alternatively, we can start a DNANexus ttyd app (see [DNANexus tools](https://documentation.dnanexus.com/user/running-apps-and-workflows/tools-list)) to use an unix shell on the browser. One of the advantages is that you can also launch https apps such as RStudio Server using this app.  [Cloud Workstation ](https://documentation.dnanexus.com/developer/cloud-workstation)is another option, but it requires installing the dx-toolkit on your local computer to ssh into it.&#x20;

### Usage

The dx-toolkit is a convenient way to interact with the DNANexus cloud platform and can almost feel like working on an HPC cluster with commands prefixed with 'dx'. It can be utilized in various ways:

1. Data Management: For example, using the `dx upload` and `dx download` command-line tools to transfer files, as well as  using the `dx describe` and `dx set_properties` commands to manage metadata associated with the files.
2. Workflow Execution: We can use  the `dx find apps` and `dx run` commands to find and run apps from the DNAnexus app store,  using the `dx new workflow` command to create a new workflow with custom apps, using the `dx wait` and `dx watch` commands to monitor the progress of the workflow execution.&#x20;
3. Custom App Development: using the `dx build` and `dx add app` commands to build DNANexus Apps (more on this in the later chapters)

### Cost

Currently, We cannot set the spending limit for a project in DNANexus, so a good practice would be setting the cost limit for each analysis, as shown below. The same command in a [bash script ](https://github.com/confluence-breast-cancer-consortia/dnanexus\_demo/blob/main/scripts/run\_plink.sh)is also on the Confluence GitHub.

```
// adding --cost-limit to limit the cost of an analysis
dx run app-swiss-army-knife \
   -iin=demo_data:Data/AMR.bed \
   -iin=demo_data:Data/AMR.bim \
   -iin=demo_data:Data/AMR.fam \
   -icmd="plink2 --bfile AMR --hwe 1e-5 --make-bed --out AMR_hwe" \
   --destination demo_analysis:/results -y \
   --cost-limit 10
```

