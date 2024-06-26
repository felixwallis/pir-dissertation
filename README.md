# Heated Debates: An Analysis of Climate Policy Speeches in UK Parliament and US Congress

## Overview

This repository contains the code for my UCL undergraduate dissertation, 'Heated Debates: An Analysis of Climate Policy Speeches in UK Parliament and US Congress'. The project aims to investigate the differences in UK and US climate policy discourse between the 1997 Kyoto Protocol and the 2015 Paris Agreement.

## Data

### Hansard Data

My dissertation investigates a corpus of UK legislative debates from 1997 to 2015. I source this corpus from Hansard, a verbatim transcript of everything MPs say in Parliament. [TheyWorkForYou.com](https://www.theyworkforyou.com/) hosts Hansard as XML files, which I download and turn into the `hansard_with_mp_details.csv` using the Python notebooks in [hansard-in-full](./hansard-in-full/). These notebooks are adapted from [scraping-political-speeches](https://github.com/nrbailey/scraping-political-speeches) by [nrbailey](https://github.com/nrbailey).

### Congressional Record Data

My dissertation also investigates a corpus of US legislative debates from 1997 to 2015. I source this corpus from the daily edition of the Congressional Record, a verbatim transcript of US House of Representatives and Senate proceedings published by Gentzkow, M., Shapiro, J.M. and Teddy, M. (2018) as [Congressional Record for the 43rd-114th Congresses: Parsed Speeches and Phrase Counts](https://data.stanford.edu/congress_text). The [congressional_record_parser.ipynb](./congressional-record/congressional_record_parser.ipynb) converts the .txt files from the dataset's `hein-daily.zip` into the `congressional_record.csv` file used in my analysis.

### Embeddings

Part of my analysis uses 840B 300 dimension GloVe embeddings to investigate the semantic differences between UK and US climate policy speeches. These can be downloaded from the [GloVe website](https://nlp.stanford.edu/projects/glove/) and saved as `glove.840B.300d.txt` in a `glove-embeddings` root directory to reproduce my work.

## [source](./source/)

The [source](./source/) directory contains my analyses' Python notebooks and R markdown files, which are structured as follows.

### [dictionaries](./source/dictionaries/)

This directory contains the code and data I use to create procedural dictionaries for Parliament and Congress and a dictionary of climate change terms:

- [shortened_congressional_record_procedural_stems.csv](/source/dictionaries/dist/shortened_congressional_record_procedural_stems.csv) contains the procedural dictionary for Congress. I adapt this dictionary from [Gennaro, G. and Ash, E. (2021) 'Emotion and Reason in Political Language'](https://doi.org/10.1093/ej/ueab104).
- [hansard_procedural_stems_creation](./source/dictionaries/hansard_procedural_stems_creation.ipynb) creates a dictionary of Parliamentary procedural terms, stored as [shortened_hansard_procedural_stems.csv](/source/dictionaries/dist/shortened_hansard_procedural_stems.csv).
- [climate_stems_creation](./source/dictionaries/climate_stems_creation.ipynb) creates a dictionary of climate change terms, stored as [shortened_climate_stems.csv](/source/dictionaries/dist/shortened_climate_stems.csv).

### [analysis](./source/analysis/)

This directory contains the code for my analyses, which is structured as follows:

- [filtering.ipynb](./source/analysis/filtering.ipynb) preprocesses the Hansard and Congressional Record data and filters it only to include climate policy speeches.
- [word_cloud_analysis](./source/analysis/word_cloud_analysis.ipynb) creates some basic word clouds of the filtered climate policy speeches. These figures provide a helpful way to ensure that the filtering process correctly captures climate policy speeches.
- [descriptive_analysis.ipynb](./source/analysis/descriptive_analysis.ipynb) performs a basic descriptive analysis of the filtered climate policy speeches.
- [word_embeddings_analysis.ipynb](./source/analysis/word_embeddings_analysis.ipynb) uses word embeddings to investigate the semantic differences between UK and US climate policy speeches.
- [topic_modelling_analysis](./source/analysis/topic_modelling_analysis.Rmd) uses structural topic models to investigate the thematic differences between UK and US climate policy speeches.
