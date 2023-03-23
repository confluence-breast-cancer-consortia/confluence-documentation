# DNANexus Apps and Applets

DNANexus offers a range of tools and apps to support genomic data analysis and management. In particular, The Swiss Army Knife app is a multi-purpose tool that can be used to run Docker images of your choice, and it comes with familiar tools such as plink2, REGENIE, QCTool, BOLT-LMM, etc.&#x20;

DNANexus allows users to develop and share their apps using open-source tools and programming languages, making it a highly customizable platform for genomic data analysis. DNANexus tools and apps provide users with a wide range of options for managing and analyzing their genomic data in a flexible and scalable environment.

The [Jupyter notebook](https://github.com/confluence-breast-cancer-consortia/dnanexus\_demo/blob/main/notebooks/bash\_demo.ipynb) we explored earlier is also a DNANexus app. We also demonstrated that instesad of downloading the plink2 binary to the Jupyter notebook VM, we can use the app-swiss-army-knife app to run plink2. While we can also run R using the R kernel on the DNANexus Jupyterlabs app;  unfortunately, DNANexus only provides RStudio Workbench to UK Biobank Research Platforms. We will create our own RStudio Server app instead.

The code source for the RStudio (and some GWAS tools) demo app is [here](https://github.com/confluence-breast-cancer-consortia/dnanexus\_demo/tree/main/apps/demo\_app). The compiled app can be used to start an RStudio server instance (username: rstudio, password:password).&#x20;

To learn more about buidling DNANexus Apps, the documentation can be found [here](https://documentation.dnanexus.com/developer/apps/intro-to-building-apps).
