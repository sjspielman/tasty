---
title: Resources for Consultation Sessions
---

Our consultation sessions are designed for you to spend your time as you would like with the support of your instructors.

You can review instruction materials, work through exercise notebooks we provide, or analyze your own data.

On this page, we've assembled some resources you may find helpful during these sessions. For more information about the structure of consultation sessions and how to get help, please review [the Consultation sessions section of the Workshop Structure page](./workshop-structure.md#consultation-days).

**Table of contents**

- [Module cheatsheets](#module-cheatsheets)
- [Working with your own data on RStudio Server](#working-with-your-own-data-on-rstudio-server)
- [Obtaining practice datasets](#obtaining-practice-datasets)
  - [Microarray data](#microarray-data)
  - [RNA-seq data](#rna-seq-data)
    - [Getting a copy of the SRAdb example notebook in your home directory on RStudio Server](#getting-a-copy-of-the-sradb-example-notebook-in-your-home-directory-on-rstudio-server)
- [Transcriptome indices for non-human organisms](#transcriptome-indices-for-non-human-organisms)
  - [_Mus musculus_](#mus-musculus)
  - [_Danio rerio_](#danio-rerio)
  - [_Canis lupus familiaris_](#canis-lupus-familiaris)

## Module cheatsheets

The [`modules-cheatsheets` directory](https://github.com/AlexsLemonade/training-modules/tree/{{site.release_tag}}/module-cheatsheets) of our [GitHub repository of training materials](https://github.com/AlexsLemonade/training-modules) contains Markdown and PDF version of "cheatsheets" that contain tables with short descriptions of functions used throughout training modules and links to documentation.

* Introduction to R/Tidyverse cheatsheet ([View Markdown](https://github.com/AlexsLemonade/training-modules/blob/{{site.release_tag}}/module-cheatsheets/intro-to-R-tidyverse-cheatsheet.md), [Download PDF](https://github.com/AlexsLemonade/training-modules/raw/{{site.release_tag}}/module-cheatsheets/intro-to-R-tidyverse-cheatsheet.pdf))
* RNA-seq module cheatsheet ([View Markdown](https://github.com/AlexsLemonade/training-modules/blob/{{site.release_tag}}/module-cheatsheets/RNA-seq-cheatsheet.md), [Download PDF](https://github.com/AlexsLemonade/training-modules/raw/{{site.release_tag}}/module-cheatsheets/RNA-seq-cheatsheet.pdf))

You may find these helpful as you review instruction material or work through exercise notebooks.

## Working with your own data on RStudio Server

If you plan on working with your own data during consultations, you may find it helpful to leverage our RStudio Server.

You can find instructions for working with your own data on RStudio Server [here](../working-with-your-data/working-with-your-own-data.md#working-with-your-own-data). **Please read these instructions carefully.**

We'll reiterate some of the most important points from those instructions below:

* As a rule of thumb, if the data you are working with would be released under controlled access, rather than made publicly available, at the time of publication of a scientific manuscript, it should not be uploaded to our RStudio Server.
* You have 50GB of space available.
If your data is larger than 50GB, please contact an instructor.

## Obtaining practice datasets

The Childhood Cancer Data Lab built and maintains [refine.bio](https://www.refine.bio/), resource of uniformly processed transcriptomic data obtained from publicly available sources.
You can read more about how we process data in refine.bio in [our documentation](http://docs.refine.bio/en/latest/index.html).

If you'd like to practice some of the skills we cover in training or gain some additional ones like making highly customizable heatmaps with the [`ComplexHeatmap`](https://bioconductor.org/packages/release/bioc/html/ComplexHeatmap.html) R package, obtaining processed data from refine.bio is a great starting point.
You may find [our examples for working with data from refine.bio](https://github.com/AlexsLemonade/refinebio-examples) helpful as you look to practice and expand your skills.
In those examples, we use R Notebooks, which you will be familiar with from this workshop!

You can start by searching [refine.bio](https://www.refine.bio/) for keywords relevant to your scientific questions and filtering to the organism and technology (e.g., microarray vs. RNA-seq; refine.bio contains both) you're interested in.

### Microarray data

In this version of our workshop, we won't work with microarray data, but there are hundreds of thousands of microarray samples available from refine.bio.
The microarray datasets you can download from the refine.bio web interface are quantile normalized and are distributed as TSV files you can read into R using functions we cover in training.
The metadata is included in your download in a TSV file that starts with `metadata_`.

### RNA-seq data

The format of the RNA-seq data you can download from the web interface of refine.bio data differs slightly from the pipeline that we cover in training.
If you identify an RNA-seq experiment from refine.bio that you'd like to use with `DESeq2` (specifically with `DESeqDataSetFromTximport`), **please send a Slack message to a CCDL instructor and they will get you access to the appropriate file.**

To retrieve metadata associated with an RNA-seq experiment (e.g., tissue, genotype), you can use an R package called [`SRAdb`](https://www.bioconductor.org/packages/release/bioc/html/SRAdb.html).
Your instructors have put together a detailed example of how to get a TSV file of sample attributes with the appropriate accession codes for use with RNA-seq data from refine.bio.

You can view a rendered version of the R Notebook with the example here: [`retrieve-SRAdb-metadata.nb.html`](https://alexslemonade.github.io/{{site.repository}}/working-with-your-data/retrieve-SRAdb-metadata.nb.html)

The relevant files from `SRAdb` have already been downloaded to the RStudio Server in the interest of space.

#### Getting a copy of the SRAdb example notebook in your home directory on RStudio Server

To get a copy of the Rmd file in your home directory that you will be able to edit, first navigate to your **Terminal**.
Make sure your current directory is your home directory by entering the following into Terminal and hitting Enter:

```sh
# Navigate to your home directory in Terminal
cd ~
```

Then you're ready to copy the file with the following command:

```sh
cp -avr shared-data/working-with-your-data/retrieve-SRAdb-metadata.Rmd
```

You can open the Rmd file as normal.

## Transcriptome indices for non-human organisms

During the introduction to bulk RNA-seq module, we use human data.
We include transcriptome indices for human in `training-modules/RNA-seq/index/`.
If you have non-human RNA-seq data you would like to quantify, we have prepared indices for select non-human organisms relevant to the study of childhood cancer.

If you have RNA-seq data for an organism that is not listed, please post in the training-specific Slack channel and let your instructors know.

### _Mus musculus_

Ensembl GRCm38 (mm10)

| File description | File use | File path |
|------------------|----------|-----------|
| Mouse Salmon index `-k 23` | Salmon index for use with `salmon quant`; appropriate for reads shorter than 75bp or for increased sensitivity with `--validateMappings` ([docs](https://salmon.readthedocs.io/en/latest/salmon.html#preparing-transcriptome-indices-mapping-based-mode)) | `~/shared-data/reference/refgenie/mm10_cdna/salmon_index/short/short` |
| Mouse Salmon index `-k 31` | Salmon index for use with `salmon quant`; appropriate for reads 75bp or longer ([docs](https://salmon.readthedocs.io/en/latest/salmon.html#preparing-transcriptome-indices-mapping-based-mode)) | `~/shared-data/reference/refgenie/mm10_cdna/salmon_index/long/long` |
| Mouse transcript to gene mapping tsv (`tx2gene`) | TSV for `tx2gene` argument to `tximport::tximport()` | `~/shared-data/reference/tx2gene/Mus_musculus.GRCm38.95_tx2gene.tsv` |

### _Danio rerio_

Ensembl GRCz11

| File description | File use | File path |
|------------------|----------|-----------|
| Zebrafish Salmon index `-k 23` | Salmon index for use with `salmon quant`; appropriate for reads shorter than 75bp or for increased sensitivity with `--validateMappings` ([docs](https://salmon.readthedocs.io/en/latest/salmon.html#preparing-transcriptome-indices-mapping-based-mode)) | `~/shared-data/reference/refgenie/z11_cdna/salmon_index/short/short` |
| Zebrafish Salmon index `-k 31` | Salmon index for use with `salmon quant`; appropriate for reads 75bp or longer ([docs](https://salmon.readthedocs.io/en/latest/salmon.html#preparing-transcriptome-indices-mapping-based-mode)) | `~/shared-data/reference/refgenie/z11_cdna/salmon_index/long/long` |
| Zebrafish transcript to gene mapping tsv (`tx2gene`) | TSV for `tx2gene` argument to `tximport::tximport()` | `~/shared-data/reference/tx2gene/Danio_rerio.GRCz11.95_tx2gene.tsv` |

### _Canis lupus familiaris_

Ensembl CanFam3.1

| File description | File use | File path |
|------------------|----------|-----------|
| Dog Salmon index `-k 23` | Salmon index for use with `salmon quant`; appropriate for reads shorter than 75bp or for increased sensitivity with `--validateMappings` ([docs](https://salmon.readthedocs.io/en/latest/salmon.html#preparing-transcriptome-indices-mapping-based-mode)) | `~/shared-data/reference/refgenie/CanFam3p1_cdna/salmon_index/short/short` |
| Dog Salmon index `-k 31` | Salmon index for use with `salmon quant`; appropriate for reads 75bp or longer ([docs](https://salmon.readthedocs.io/en/latest/salmon.html#preparing-transcriptome-indices-mapping-based-mode)) | `~/shared-data/reference/refgenie/CanFam3p1_cdna/salmon_index/long/long` |
| Dog transcript to gene mapping tsv (`tx2gene`) | TSV for `tx2gene` argument to `tximport::tximport()` | `~/shared-data/reference/tx2gene/Canis_familiaris.CanFam3.1.95_tx2gene.tsv` |
