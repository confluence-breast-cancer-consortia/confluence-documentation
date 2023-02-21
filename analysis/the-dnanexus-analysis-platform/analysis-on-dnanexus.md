# Analysis on DNAnexus

### Finding available analysis tools on DNANexus

Briefly, DNANexus tools can be found under the [Tools](https://platform.dnanexus.com/panx/tools) tab.&#x20;

### Analysis Docker image

Ideally, each program should have their own Docker container. However, for testing, we will create a container that has most of the standard software. The Rstudio Server app is run by creating a HTTPS app from the Docker image. And the same Docker image can also be used to run command line jobs. Currently, a Docker image containing RStudio Server, plink 1.9 and 2.0, GCTA and ldscore is created and can be pulled from https://hub.docker.com/repository/docker/shukwong/rstudio\_with\_gwas\_tools&#x20;

{% hint style="info" %}
Caveats:

1. The default entry point for the Docker image is to start the RStudio service, but if the command, e.g. plink2 is supplied, plink will be run instead.
2. ldscore require python 2.7, while most of the python programs are now using python 3.9. For this reason, a separate conda environment was installed for ldsc, to run ldsc, you will need to activate the ldsc conda environment by: source /opt/conda/bin/activate ldsc
{% endhint %}



### Running RStudio on DNAnexus&#x20;

{% code overflow="wrap" %}
```markdown
An applet called test_app has been created from the Docker image mentioned above
(https://github.com/shukwong/pipelines/tree/master/dnanexus/test_app) and has been placed in DNANexus projects concept1 and DCEG2. Note that unlike an app, an applet is bound to the project and can only be copied within the same region.

Click the test_app to start it, when it’s running, click on the job link to log into RStudio (user: rstudio,password:password). Currently, this app is using the Docker image mentioned above, it installs additional R packages on top of the Rocker tidyverse image, (along with plink binaries etc)
See [here](https://raw.githubusercontent.com/shukwong/pipelines/master/docker_images/rstudio_with_gwas_tools/install_r_packages.sh) for the R package installation script 
```
{% endcode %}



### Monitoring analysis progress

You can use the web interface or the command line interface to monitor DNANexus analysis progress.&#x20;

#### Using Command Line

1. Open a terminal or command prompt and log in to your DNAnexus account using the `dx login` command.
2. Navigate to the project that contains the analysis you want to monitor using the `dx cd` command.
3. Use the `dx watch` command to monitor the analysis progress. This command will display real-time updates on the analysis status and progress.

For example, to monitor an analysis with the ID "analysis-XXXX", you can run the following command:

```
dx watch analysis-XXXX
```

### Retrieving and viewing analysis results
