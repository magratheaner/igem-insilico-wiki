# igem-insilico-wiki

This repository (and especially this readme) is meant to be a comprehensive central hub for links to and explanations of all resources and experiments of the insilico team. 

The goal is for you to be able to find what you're looking for fast, whether you want to use the most recent cleaned version of a specific dataset, do an analysis on an existing model, or think about what we haven't tried yet.

> Please feel free to submit a pull request with missing information to this repository

## Table of Contents

- [Resources](#resources)
	- [Spreadsheets](#spreadsheets)
	- [Tools for team organization](#tools-for-team-organization)
- [Data](#data)
	- [BacDive+](#bacdive)
	- [ProtDataTherm](#protdatatherm)
	- [HotMuSiC](#hotmusic)
- [Experiments](#experiments)
 	- [by task](#by-task)
	- [by dataset](#by-dataset)
	- [by model architecture](#by-model-architecture)
- [Tools](#tools)

## Resources

### Spreadsheets

[List of datasets](https://docs.google.com/spreadsheets/d/12qQ44Lixufg1sL74ecqR1nrn7GDrgzPgbs6Nozlt7oc) (central place for meta information (e.g. references, sample size, features) about all datasets we found in the literature)

[List of protein features](https://docs.google.com/spreadsheets/d/172l6AUkrFuAEUf2WOngdpZwuumLaQ0EeclDqBlsGuqg) (central collection of information (e.g. meaning, how to determine) on all protein/amino acid features we have seen used in the literature)

[List of models and results from the literature](https://docs.google.com/spreadsheets/d/1B2Oichih2ULUcHTRMuYThzdM8plzfmSx-v9ggxMMeCk) (a bit more concise of an overview than Zotero summaries to properly compare paper results and models)

### Tools for team organization

We use these tools to communicate with each other, as programming frameworks, or to keep data and visualizations in a central place. 

#### General tools

Ideally you would visit these links regularly and have a good idea of their current contents.

It may be advisable to put these links into an iGEM bookmark folder in your browser to have them at your hands.

- [Slack workspace](https://igem2019.slack.com) (main way of communicating progress and discussing problems)
- [Trello group](https://trello.com/igem20192) (main way of keeping track of tasks and their individual progress)
- [Box.UP storage](https://boxup.uni-potsdam.de/index.php/s/36GhHodbtqGx6Ul) (50GB of storage for mirroring datasets and visualizations in a central location, ask for password in Slack)
- [Zotero group](https://www.zotero.org/groups/2232261/igem_potsdam_2019) (repository for papers and summaries thereof, for a usage guide see [here](https://docs.google.com/document/d/131G6tTeI5Y4NjsgYtGfrgqzANEyL1vli0CHTWTwS-9w))

#### Programming tools and frameworks

Generally, we try to use Python in our solutions to keep the barrier of reading others' code as low as possible.

> Please also think about how to make your code reusable (a notebook should just use reusable external functions (libraries) in a certain order, not really implement stuff itself)

- [Google Colab](https://colab.research.google.com/) (like Google Docs but for Python Notebooks, easy use of ML frameworks)
- [Keras](https://keras.io/) (easy-to-use Python ML library for building neural nets of all sorts)
- [BioPython](https://biopython.org/) (often useful for reading/writing typical file formats (e.g. FASTA, PDB))

## Data

### BacDive+

A dataset that connects protein sequences to the growth temperatures of their containing organisms. 

We created it specifically for this project by using both the [BacDive](https://bacdive.dsmz.de/) API and the BioPython NCBI Entrez API. The crawler code can be found in [this repository](https://gitlab.com/magratheaner/bacdive-thermal-data).

It consists of two parts:
1. `df_ncbi.csv`: ~8 mil. (1 mil. thermo, 7 mil. meso) protein sequences that are linked to BacDive organism IDs 
2. `df_bacdive.csv`: ~30k organism IDs that are linked to temperature test information crawled from BacDive

[CSV files on Google Drive](https://drive.google.com/drive/folders/1jyUBTfdGp5NARN-fynDSqqML85F22A6U) (for better integration into Google Colab just copy over the file to your Drive instead of down- and reuploading)
Location on Box.UP: `in silico/Data/BacDive+`

### ProtDataTherm

Described in [this paper](https://www.zotero.org/groups/2232261/igem_potsdam_2019/items/collectionKey/6IIJYPQ9/itemKey/9YYSW2GL) (link to Zotero entry with summary) the ProtDataTherm dataset claims to offer ~600k thermostable (Tm >40°C) proteins categorized by domain families (Pfams). Although it is badly cleaned and only available via an intransparent web interface, most of our experiments have been based on it since it was the only dataset of substantial size before the BacDive+ dataset.

[Numpy files (.npy) on Google Drive](https://drive.google.com/drive/folders/1oOkUYSJXy8NUP1sQ5U0GQFNvSuwdjU67) (esp. `pdt_X_unique_huge.npy`) (for better integration into Google Colab just copy over the file to your Drive instead of down- and reuploading)

### HotMuSiC

#### HotMuSiC v2.0

This version contains mutated protein sequences and some added features. It accounts for frameshifts of the protein sequences (not starting at 0) (check column `OFFSET_SEQUENCE`) and keeps all of the original features in place.

[CSV file on Google Drive](https://drive.google.com/open?id=1-4-wFMtTZKfVBLcvQtVcCd26NtgXFmmc) ([containing folder](https://drive.google.com/drive/folders/1H6YCUINDRcRyHbCgHjE1IPSKHdfQaWBG))

#### HotMuSiC v1.1 (with mutated protein sequences)

Added downloaded protein sequences and inserted mutations. Wildtype rows are identified by `mutation_counter = 0` and `Delta_T_m = 0.0`.

> Warning: the .csv file doesn't contain a header row yet, this should be fixed. 
> In the meantime here are the column header names as comma-separated text: 
> `PDB-ID`, `Delta_T_m`, `T_m`, `sequence`, `mutation_counter`

[CSV file on Google Drive](https://drive.google.com/file/d/1VhDAXY0B_wf4H5X4eP-YB9LRzqZnmyOU/view)

#### original HotMuSiC (v1.0)

The original version of the HotMuSiC dataset as created by the research group of Pucci et al. is not of much use in its unaltered state since there are no protein sequences, only PDB IDs and uninserted point mutations.

[Official download from `babylone.ulb.ac.be`](http://babylone.ulb.ac.be/HotPots/index.php)

Mirrored copy on our BoxUp under `/in silico/Data/HotMuSiC` 

## Experiments

This section is meant to be a collection of all the best (status-quo) models we have learned until now, categorized by the problem they solve, which dataset was used for training, and which model architecture was used.

> To the authors of models: please decide on a few best models per subcategory (e.g. for Classification your best classifier, for ProtDataTherm your best model using this dataset as training) to avoid this section getting too cluttered

### by task

#### Classification (thermo/meso)

#### Regression (exact melting temperature)

[Regressor on HotMuSiC](https://drive.google.com/drive/folders/1HXpnmiGfUownb6IyovLwPO4_bxhp0EtZ) (96 MSE on .15 split)

#### Generation (predict best mutation)

### by dataset

#### ProtDataTherm

#### BacDive+

### by model architecture

#### Dense

#### CNN

## Tools
