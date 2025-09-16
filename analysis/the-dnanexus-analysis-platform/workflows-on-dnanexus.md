# Workflows on DNAnexus

### A. Creating a Nextflow workflow on DNAnexus&#x20;

For detailed, step-by-step instructions on creating and running Nextflow workflows on DNAnexus, please refer to the official documentation: [Running Nextflow Pipelines](https://documentation.dnanexus.com/user/running-apps-and-workflows/running-nextflow-pipelines). This resource provides comprehensive guidance and best practices for using Nextflow on the DNAnexus platform.

The easiest way to build a nextflow workflow is point to to the cloned repo as follows, this will build an applet that lives only in the project. Please make sure the applet has view access to other projects: 

```bash
dx build --nextflow --extra-args '{"access":{"allProjects":"VIEW"}}' <nextflow_workflow_directory>
```

### B. Running a Nextflow workflow on DNAnexus

If the nextflow applet was built successfully, you should see the ID for the applet that looks like applet-xxxx, you can run it by:

```bash
dx run applet-xxxx ... \
-i ...
```

The -i argument modifies the default parameters. For example
```bash
-i nextflow_run_opts="-profile docker -queue-size 100" 
```
changes the profile to docker (defined in the config), and increase the number of concurrent jobs to 100.

```bash
-i nextflow_soft_confs=<path_to_config_on_dnanexus>
```
allows user to change the workflow related parameters 

```bash
-i preserve_cache=true 
```
and
```bash
-i resume="<session_id>"
```
allows the intermediate files of the workflow to be cached so it can be resumed later. See [here](https://documentation.dnanexus.com/user/running-apps-and-workflows/running-nextflow-pipelines#nextflow-resume) for more details. Please note that currently only 20 cached sessions are allowed per project and it would be a good idea to clean up or move the cached working directories once you have a successful run. 