# Computational laboratory for BIOL 550 Systematics

> **NOTE** 
> This was developed/organized for a class at Humboldt State University for the spring of 2022. 
> Some of the material has beed modified from another workshop repository that I co-authored with Merly Escalona at UCSC [Intro to computational tools at UCSC](https://github.com/merlyescalona/ucsc-eeb-intro2comptools) 

The aim of the lab is to provide students the skills necessary to analyse data from next-geneeration sequencing using phylogenetic methods. Studnts will first learn how to use the command line, then will learn how to use an array of phylgentic software, and finally will gain some skills in python and R coding.

These tutorials are hands-on and were designed to be followed on a Linux machine with all the software pre-installed. However, a list of software can be found at the bottom of this page for your reference.

## What to expect?

At the end of the course participants will be comfortable using the bash environment, using phylogentic software, and writing basic python and R scripts.

## Coneccting to HSU virtual labs

Every week in lab you will connect to a Linux virtual machine. There are two ways of connecting to the virtual machine:

1. log in with HSU credetials into the [vlinux.humboldt.edu](https://vlinux.humboldt.edu/) This should work smoothly in your computer station at the lab and possibly in your own laptop.

2. Install NoMachine in your laptop. [Installation instructions](https://its.humboldt.edu/vlinux-home-instructions)

## Weekly program (subject to change):

[W-1](https://github.com/oscarvargash/biol_550_2022/tree/main/week_01) Introduction to bash, using FastQC

[W-2] Quality control of raw reads, BBtools, BBduk

[W-3] Assemblage of sequences from short reads,
SAMtools, sam2consensus, BCFtools, IGV genome viewer

[W-4] GenBank, Git, DNA alignment, MAFFT, AliView

[W-5] PAUP, IQTREE, Figtree,

[W-6] Project proposal presentation and submission

[W-7] Beauti and the BEAST (and dependents -Tracer), MrBayes

[W-8] Introduction to Phyton

[W-9] Loops in Python

[W-10] No class

[W-11] BEAST, chronogram inference + Project dataset submission

[W-12] Tree visualization and manipulation in R

[W-13] Character tracing in R

[W-14] Connecting to a computer cluster ssh

[W-15] Final project presentations


# Instructor:

[Oscar Vargas](http://oscarmvargas.com/) (<ov20@humboldt.edu>): botanist and evolutionary biologist, experience with bioinformatics and phylogenomics. Assistant Professor at Humboldt State University.

# Appendix, software used in the tutorials

Here is a list of the software associated with the lab. You do not need to install these in your machine unless you really want to. This software has been installed in the virtual Linux machines of HSU.

[BBtools](https://jgi.doe.gov/data-and-tools/bbtools/bb-tools-user-guide/installation-guide/)

[FastQC](https://www.bioinformatics.babraham.ac.uk/projects/fastqc/)

[SAMtools](http://www.htslib.org/)

[Integrative Genomics Viewer (IGV)](https://software.broadinstitute.org/software/igv/)

[MAFFT](https://mafft.cbrc.jp/alignment/software/)

[AliView](https://ormbunkar.se/aliview/)

[PAUP](https://paup.phylosolutions.com/get-paup/)

[IQTREE](http://www.iqtree.org/)

[Figtree](http://tree.bio.ed.ac.uk/software/figtree/)

[BEAST](https://github.com/beast-dev/beast-mcmc)

[Tracer](https://github.com/beast-dev/tracer/releases)

[MrBayes](https://nbisweden.github.io/MrBayes/download.html)

Linux programs: git, ssh

Python3 modules: pandas, numpy, sys, os, re, operator, argparse, gzip, math, biopython

R packages: phytools, maps, ape, ggplot2


