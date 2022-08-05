<p align="center">
  <img src="MetaCoAG_Logo.png" width="500" title="MetaCoAG logo" alt="MetaCoAG logo">
</p>

# MetaCoAG: Binning Metagenomic Contigs via Composition, Coverage and Assembly Graphs

[![CI](https://github.com/metagentools/MetaCoAG/actions/workflows/testing.yml/badge.svg)](https://github.com/metagentools/MetaCoAG/actions/workflows/testing.yml)
![GitHub](https://img.shields.io/github/license/Vini2/MetaCoAG)
[![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/psf/black)
![GitHub](https://img.shields.io/github/v/release/Vini2/MetaCoAG?include_prereleases)
[![Documentation Status](https://readthedocs.org/projects/metacoag/badge/?version=latest)](https://metacoag.readthedocs.io/en/latest/?badge=latest)

MetaCoAG is a metagenomic contig binning tool that makes use of the connectivity information found in assembly graphs, apart from the composition and coverage information. MetaCoAG makes use of single-copy marker genes along with a graph matching technique and a label propagation technique to bin contigs. MetaCoAG is tested on contigs obtained from next-generation sequencing (NGS) data. Currently, MetaCoAG supports contigs assembled using metaSPAdes and MEGAHIT, and recently we have added support for Flye assemblies (has not been tested extensively).

For detailed instructions on installation, usage and visualisation, please refer to the [documentation hosted at Read the Docs](https://metacoag.readthedocs.io/).

**NEW:** The conda package of MetaCoAG is now available on bioconda at 
[https://anaconda.org/bioconda/metacoag](https://anaconda.org/bioconda/metacoag).

## Dependencies
MetaCoAG installation requires Python 3.7 or above (tested on Python 3.7.4). You will need the following python dependencies to run MetaCoAG and related support scripts. The tested versions of the dependencies are listed as well.
* [python-igraph](https://igraph.org/python/) - version 0.9.6
* [biopython](https://biopython.org/) - version 1.74
* [networkx](https://networkx.github.io/) - version 2.4
* [scipy](https://www.scipy.org/) - version 1.3.1
* [numpy](https://numpy.org/) - version 1.17.2
* [tqdm](https://github.com/tqdm/tqdm) - version 4.36.1

MetaCoAG uses the following tools to scan for single-copy marker genes. These tools are included with the following versions.
* [FragGeneScan](https://sourceforge.net/projects/fraggenescan/) - version 1.31
* [HMMER](http://hmmer.org/) - version 3.3.2


## Installing MetaCoAG using conda

You can install MetaCoAG via [Conda](https://docs.conda.io/en/latest/) from [bioconda](https://anaconda.org/bioconda/metacoag).

```
# add channels
conda config --add channels defaults
conda config --add channels bioconda
conda config --add channels conda-forge

# create conda environment
conda create -n metacoag

# activate conda environment
conda activate graphbin

# install metacoag
conda install -c bioconda metacoag

# check metacoag installation
metacoag -h
```

## Setting up MetaCoAG for development

### Downloading MetaCoAG
You can clone the MetaCoAG repository to your machine.

```
git clone https://github.com/Vini2/MetaCoAG.git
```

Now go into the MetaCoAG folder using the command

```
cd MetaCoAG/
```

### Setting up the environment
We recommend that you use [Conda](https://docs.conda.io/en/latest/) to run MetaCoAG.

Once you have installed Conda, make sure you are in the MetaCoAG folder. Now run the following commands to create a Conda environment and activate it to run MetaCoAG.

```
conda env create -f environment.yml
conda activate metacoag
```

## Example Usage

```
metacoag --assembler spades --graph /path/to/graph_file.gfa --contigs /path/to/contigs.fasta --paths /path/to/paths_file.paths --abundance /path/to/abundance.tsv --output /path/to/output_folder
```

```
metacoag --assembler megahit --graph /path/to/graph_file.gfa --contigs /path/to/contigs.fasta --abundance /path/to/abundance.tsv --output /path/to/output_folder
```

```
metacoag --assembler flye --graph /path/to/assembly_graph.gfa --contigs /path/to/assembly.fasta --paths /path/to/assembly_info.txt --abundance /path/to/abundance.tsv --output /path/to/output_folder
```


## Citation

MetaCoAG has been accepted at [RECOMB 2022](https://recomb2022.net/accepted-papers/) and is published in Lecture Notes in Computer Science at [https://doi.org/10.1007/978-3-031-04749-7_5](https://doi.org/10.1007/978-3-031-04749-7_5).

If you use MetaCoAG in your work, please cite as,

```bibtex
@InProceedings{10.1007/978-3-031-04749-7_5,
  author="Mallawaarachchi, Vijini and Lin, Yu",
  editor="Pe'er, Itsik",
  title="MetaCoAG: Binning Metagenomic Contigs via Composition, Coverage and Assembly Graphs",
  booktitle="Research in Computational Molecular Biology",
  year="2022",
  publisher="Springer International Publishing",
  address="Cham",
  pages="70--85",
  abstract="Metagenomics has allowed us to obtain various genetic material from different species and gain valuable insights into microbial communities. Binning plays an important role in the early stages of metagenomic analysis pipelines. A typical pipeline in metagenomics binning is to assemble short reads into longer contigs and then bin into groups representing different species in the metagenomic sample. While existing binning tools bin metagenomic contigs, they do not make use of the assembly graphs that produce such assemblies. Here we propose MetaCoAG, a tool that utilizes assembly graphs with the composition and coverage information to bin metagenomic contigs. MetaCoAG uses single-copy marker genes to estimate the number of initial bins, assigns contigs into bins iteratively and adjusts the number of bins dynamically throughout the binning process. Experimental results on simulated and real datasets demonstrate that MetaCoAG significantly outperforms state-of-the-art binning tools, producing similar or more high-quality bins than the second-best tool. To the best of our knowledge, MetaCoAG is the first stand-alone contig-binning tool to make direct use of the assembly graph information.",
  isbn="978-3-031-04749-7"
}
```
