# `pmda` R-source pipeline

`pmda` is an R pipeline for finding Differentially Methylated Regions (DMR) between different experimental conditions of a specific region of a DNA sequence, whose samples have been treated with bisulfite and sequenced with a 454 GS FLX system.

__Contents__

1. Licensing
2. Overview
3. Requirements
4. Installation
5. Documentation
6. NOTE
7. Authors

## 1. Licensing

`pmda` - R-source pipeline for finding Differentially Methylated Regions (DMR) v 1.0.1 - Copyright (c) 2015 Jose Luis Mosquera - jlmosquera@gmail.com

Use and distribution subject to the terms of the GPL-2 license. See LICENSE for details.


## 2. Overview

`pmda` is a pipeline devoted to slecte differentially methylatedregions between different experimental conditions of a specific region of a DNA sequence, whose samples have been treated with bisulfite and sequenced with a 454 GS FLX system from Roche. Five main processes have been implemented. Specifically:

 * __Process 1: Quality Control of Raw Data__

Performs a quality assessment and checks on raw reads generated by the sequencer.
   
 * __Process 2: Preprocessing__
 
Prepares raw data for the alignment process, sequence reads are:

    * filtered,
    * splitted, and
    * trimmed 

according to different criteria.

 * __Process 3: Alignment__

Maps preprocessed reads against the reference sequence and identification of methylated sites.

 * __Process 4: Quantification__

It is devoted to quantify (un)methylation for each context, amplicon and site, but this process performs different steps. Specically, `pmda` carries out

    * a quality assessment of the alignment process,
    * constructs methylation matrices associated with each context (i.e. CG, CHG or CHH), and 
    * quantifies the methylation measures for each sample and target region (i.e. gene).

It computes beta-values and also M-values

 * __Process 5: Selection of DMR__

Based on  Fisher's Exact Tests for each site, corrected by FDR, finds the differentially methylated regions between the experimental conditions.

## 3. Requirements

To use the pipeline one must have `R 3.2` (or greater) installed, as well `Bioconduictor 3.1` (or greater). But also, some extra packages from CRAN are required. Specifically, `ShortRead`, `tools`, `reshape2`, `parallel`, and `gplots`. It is also essential to have `Perl 5 18.2`, [FastQC](http://www.bioinformatics.babraham.ac.uk/projects/fastqc/) and [BiQ Analyzer HT](http://biq-analyzer-ht.bioinf.mpi-inf.mpg.de/) well installed.

## 4. Installation

1. Download and uncompress `pmda.zip`
2. Create your project folder `./<your_project>/`
3. Copy the uncompressed files into your folder `cp pmda/ ./<your_project>/`
4. Create a `mkdir ./<your_project>/data/`
5. Create a `mkdir ./<your_project>/data/run/`
6. In `run/` save your raw data, that is, the `<raw_reads>.fasta` and `<raw_reads>.qual` files
7. In `data/` save the files associated with the experiments: `lanes.csv`, `mids.csv`, `primers.csv`, `refseq.fasta`, `samples.csv`, `targets.csv`, `comparisons`.


## 5. Documentation

Currently there is neither a reference manual nor a vignette. But each source has a brief description. Moreover, functions in sources placed at the folder `functions` are better documented.

Next release will be packaged all the cource of the pipeline and it will be well documented.


## 6. NOTE

`pdma` is an R-source developed as a part of the Master's thesis called *_Methylation Data Analysis Associated with Alzheimer's Disease_* at the [University of Vic - Central University of Catalonia](http://mon.uvic.cat/master-omics/).

## 7. Authors

* Msc candidate (Author and Mantainer): Jose Luis Mosquera, PhD (jlmosquera@gmail.com) - Department of Systems Biology. University of Vic - Central University of Catalonia
* Supervisor: Malu Calle Rosingana, PhD - Department of Systems Biology. University of Vic - Central University of Catalonia
* Co-supervisor: Marta Barrachina Castillo, PhD - Institute of Neuropathology - Bellvitge University Hospital

