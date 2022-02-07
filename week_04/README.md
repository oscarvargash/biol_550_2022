# Week four: DNA alignments and loops

> Add the yellow flag to the right corner of your screen ![](img/yellow.jpeg)

To start this tutorial you need to be logged in the Linux virtual machine
[vlinux.humboldt.edu](https://vlinux.humboldt.edu/)

Once logged in the Linux machine, look for the Terminal, it is an icon that contains the characters `>\_`

You can also write `terminal` in the search bar of the main manu located in the left bottom of the operating system.

## Aligning DNA matrices

Now that we have been able assemble a DNA regions we can aling those using aligning tools. There are many tools out there to perform aligments, today we will we use mafft.

### Download data

Make a folder for this week:

```
cd Documents
mkdir week_04
cd week_04
```

Download data from genbank:

[https://www.ncbi.nlm.nih.gov/genbank/](https://www.ncbi.nlm.nih.gov/genbank/)

In the search bar type:

```
Diplostephium internal transcribed spacer
```

Select the first 10 results, then download the data:

1. Click on `send to` at the top right
2. Select the `file` option
3. Select the `fasta` format
4. Click on `create file`
5. Select `save file`
6. move the file to `week_04` from `Downloads`

```
mv ~/Downloads/sequence.fasta .
cat sequence.fasta
```

> Change your flag to green if you are good to continue ![](img/green.jpeg)

### Vizualizing and creating alignments

> Add the yellow flag to the right corner of your screen ![](img/yellow.jpeg)

We can vizlualize the fasta file that we downloaded with `aliview`

```
aliview sequence.fasta 
```

A new windown has been opened, here you can navigate this matrix that has not been aligned. Close the program when you are done and return to the terminal.

Let's make an aligment of for this matrix. We sill use `mafft`, which is one of many tools available. [mafft website](https://mafft.cbrc.jp/alignment/software/algorithms/algorithms.html) contains useful information about the types of algoriths emplyed in the program, and how they compare to other software.

Because we have only have 10 sequences, we will use a computational expensive algorith:

```
mafft --maxiterate 1000 --localpair sequence.fasta > sequence.al.fasta 
aliview sequence.al.fasta
```

Congratulations, you have created your first alignment!

> Change your flag to green if you are good to continue ![](img/green.jpeg)





> Add the yellow flag to the right corner of your screen ![](img/yellow.jpeg)






Let's unzip the data 

```
unzip files_w3.zip
```

> Change your flag to green if you are good to continue ![](img/green.jpeg)

### Download reference

GenBank is a repository of DNA sequences, it contains (in theory) sequences for every single pusblished study that has use DNA.

![](img/gb.png)

> Add the yellow flag to the right corner of your screen ![](img/yellow.jpeg)

We will download our reference from GenBank. Our data is a subset of genomic reads that correspond the nuclear ribosomal RNA. Inside your virtual linux go to:

[https://www.ncbi.nlm.nih.gov/genbank/](https://www.ncbi.nlm.nih.gov/genbank/)


In the search bar type:

```
Diplostephium internal transcribed spacer
```

Click on the first result. This page shows the sequence in GenBank format. A useful format for mapping is the fasta format. To download the seqeuence in fasta format do the following.

1. Click on `send to` at the top right
2. Select the `file` option
3. Select the `fasta` format
4. Click on `create file`
5. Select `save file`
6. move the file to `week_03` from `Downloads`


How can we move `sequence.fasta` into `week_03` from `Downloads` in the terminal?

<details>
  <summary>Click to see an answer!</summary>
  
In the terminal, while located in `week_03` you can type:

```
mv ~/Downloads/sequence.fasta .
```

</details>

> Change your flag to green if you are good to continue ![](img/green.jpeg)

### Performing the mapping

> Add the yellow flag to the right corner of your laptop ![](img/yellow.jpeg)


First we need to create a reference. This step creates a database for bbmap of the reference.

```
bbmap.sh ref=sequence.fasta
```

Now we can do the mapping, note that our input is the two read files and our output is a `*.sam` file. This command also creates a script than later creates a `*.bam` file which, we will use to vizulize the mapping

```
bbwrap.sh in1=Diplostephium_azureum_R1_nrmap.fastq.gz in2=Diplostephium_azureum_R2_nrmap.fastq.gz outm=D_azur.sam append ref=sequence.fasta nodisk bamscript=bs.sh

ls 
```

Now let's create the bam file:

```
sh bs.sh
```

Finally we create the consesus using a python2 script

```
python2 sam2consensus.py -i D_azur.sam
cat KX063971.1__D_azur.fasta
```

> Change your flag to green if you are good to continue ![](img/green.jpeg)


### Vizualizing the mapping

> Add the yellow flag to the right corner of your laptop ![](img/yellow.jpeg)


We can vizualize the mapping by using the Integrative Genomics Viewer. Open the application by:

```
igv.sh
```

Load the reference sequence:

1. Click on `Genomes`
2. Click on `Load Genome from File`
3. Load `sequence.fasta` from your folder in `week_03`

You should be able to see the loaded reference of 9,238 base pairs

![](img/igv1.png)

Load the mapping file `D_azur_sorted.bam`

1. Click on `file`
2. Click on `Load from File`
3. Load `D_azur_sorted.bam`

You should be able to see the mapping now

![](img/igv2.png)

> Change your flag to green if you are good to continue ![](img/green.jpeg)


### Exercise

Navigate the mapping in IGV and answer the following questions:

1. Do the reads match exactly the reference?
2. Identify at least two problematic regions, indicate their coordinates (in base pairs) and why you think these are problematic.
3. (optional) Map the reads to the consensus sequence `KX063971.1__D_azur.fasta`, are those problems solved?

