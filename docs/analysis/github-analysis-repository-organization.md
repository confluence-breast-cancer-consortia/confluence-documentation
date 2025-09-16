# GitHub analysis repository organization

While there is no one "right" way to organize a GitHub repository,  here's our suggested structure:

```markdown

├── data
├── scripts
│   ├── preprocessing
│   ├── analysis
│   └── visualization
├── results
│   ├── figures
│   ├── tables
│   └── reports
├── docker
├── environment.yml
├── README.md
```

* `data`: This directory contains analysis data, as well as metadata files. Please do not commit individual-level data to GitHub
* `scripts`: This directory contains subdirectories for different types of scripts, such as preprocessing, analysis, and visualization.&#x20;
* `results`: This directory contains subdirectories for different types of results, such as figures, tables, and reports.&#x20;
* `docker directory or environment.yml`: The docker directory contains the Docker file for the reproducible computational environment for the analysis.  Alternatively, if you are using Python, this environment.yml file contains a specification of the software environment required to run the code in the repository.&#x20;
* `README.md`: This file contains information about the repository, including a brief description of the project, instructions for running the code, and any other relevant information.

``
