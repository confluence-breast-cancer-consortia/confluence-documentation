# Confluence Workflows and Tools


## Available Workflows

### regenie workflow for GWAS

We have forked and modified the [nf-gwas](https://github.com/genepi/nf-gwas) nextflow workflow for Confluence analysis. It's on Confluence GitHub at [https://github.com/confluence-breast-cancer-consortia/nf-gwas](https://github.com/confluence-breast-cancer-consortia/nf-gwas). The release with tag confluence-v0.1 was imported to the *confluence-concept-1-analyses* project in DNAnexus as an [applet](https://documentation.dnanexus.com/faqs/developing-apps-and-applets). Please note that the base Docker image for the nf-gwas workflow was also modified and is hosted [here](https://github.com/orgs/confluence-breast-cancer-consortia/packages/container/package/nf-gwas) under the Confluence GitHub packages. 

Below is a sample command line for running the nf-gwas workflow on DNAnexus. This requires using dx-toolkit on your local computer. Please refer to the [dx-toolkit](https://confluence-breast-cancer-consortia.github.io/confluence-documentation/demo/dx-toolkit/) section under Demo to learn how to use dx-toolkit. 

```bash
dx run applet-J3264V04kqq6GZKYYbB4jY58 \
    -i nextflow_run_opts="-profile docker -queue-size 250" \
    -i outdir=<output_directory_name> \
    -i preserve_cache=true \
    -i nextflow_soft_confs=/tools/nf-gwas-applet/configs/2cpuForStep2_loocv_report.config \
    -i nextflow_pipeline_params="--project <uniqueNameForYourProject> \
    --container ghcr.io/confluence-breast-cancer-consortia/nf-gwas:regenie4.1-bgenix \
    --genotypes_prediction_bed dx://project-<project_id>:/<path_to_genotype_bed_file> \
    --genotypes_prediction_bim dx://project-<project_id>:/<path_to_genotype_bim_file> \
    --genotypes_prediction_fam dx://project-<project_id>:/<path_to_genotype_fam_file> \
    --genotypes_association dx://project-<project_id>:/<path_to_imputed_data>/chr*/*.bgen \
    --regenie_sample_file dx://project-<project_id>:/<path_to_one_of_the_bgen.samples_file> \
    --association_build hg38 --genotypes_association_format bgen \
    --phenotypes_filename dx://project-<project_id>:/<path_to_phenotype_file> \
    --phenotypes_columns BreastCancer --phenotypes_binary_trait true \
    --covariates_filename dx://project-<project_id>:/<path_to_covariates_file> \
    --covariates_columns PC1,PC2,PC3,PC4,PC5,PC6,PC7,PC8,PC9,PC10 --regenie_test additive --prune_enabled true \
    --prune_maf 0.05 --qc_maf 0.02 --qc_mac 0 --qc_geno 0.05 --qc_hwe 0 --qc_mind 0.05 --regenie_min_mac 30 \
    --regenie_min_imputation_score 0.2 --annotation_min_log10p 2 \
    --rsids_filename dx://project-GzJXf184kqq1512KkxGJ6f3Y:/data-annotation/rsids-v154-hg38.index.gz" \
    --destination project-GzJXf184kqq1512KkxGJ6f3Y:/<directory_on_dnanexus>/ --brief -y
```

## Available Tools

### rstudio with gwas tools

We have updated the R Studio Docker image to be used on DNAnexus [here](https://github.com/orgs/confluence-breast-cancer-consortia/packages/container/package/rstudio_with_gwas_tools). The DockerFile is [here](https://github.com/shukwong/pipelines/blob/master/docker_images/rstudio_with_gwas_tools/Dockerfile). Please feel free to modify this or create your own Docker image to be used on DNAnexus.  

Below is an example of using the docker image with swiss-army-knife to plot manhatten and qq plots using an R script.

```bash
dx run app-swiss-army-knife \
   -iimage="ghcr.io/confluence-breast-cancer-consortia/rstudio_with_gwas_tools:v1.0" \
   -iin=tools/scripts/manhattan_qq_plot.R \
   -iin=<project_name>:<path_to_summary_stat_file> \
   -icmd="Rscript manhattan_qq_plot.R --input_file <summary_stat_file> --outdir <output_directory> --num_cases <num_cases> --num_controls <num_controls>" \
   --destination <project_name>:/<output_directory_on_dnanexus> -y 
```   

## Support

For questions or issues with Confluence workflows and tools, please use the relevant issues and discussions on Confluence GitHub repositories.
