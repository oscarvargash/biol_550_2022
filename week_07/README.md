# Week seven: building trees using Maximum Likelihood with iqTree

> Add the yellow flag to the right corner of your screen ![](img/yellow.jpeg)

To start this tutorial you need to be logged in the Linux virtual machine
[vlinux.humboldt.edu](https://vlinux.humboldt.edu/)

Once logged in the Linux machine, look for the Terminal, it is an icon that contains the characters `>\_`

You can also write `terminal` in the search bar of the main manu located in the left bottom of the operating system.

### Download data

Make a folder for this week:

```
cd Documents
mkdir week_07
cd week_07
```

Download and unzip data from this lab:

```
wget https://github.com/oscarvargash/biol_550_2022/raw/main/week_07/files/files.zip
unzip files.zip
```

> Change your flag to green if you are good to continue ![](img/green.jpeg)

### Testing models of evolution in the alignments

> Add the yellow flag to the right corner of your screen ![](img/yellow.jpeg)

Every DNA region can be modeled using different DNA models of subsitition, we can perform a test in IQtree to infer the best model for each DNA region:

First we can see how iqtree operates:

```
iqtree
```

Now we can do the test for a single gene

```
iqtree -s ccsA-ndhD.fasta -m MF
```

In the output we can see that `iqtree` perform multiple tests in all the possible models. The [iqtree website](http://www.iqtree.org/doc/) contains useful information for interpreting outputs.

> Change your flag to green if you are good to continue ![](img/green.jpeg)

### Performing a Maximum Likelihood tree search

> Add the yellow flag to the right corner of your screen ![](img/yellow.jpeg)

`iqtree` is currently the fastest and more accurate program to infer phylogenies using maximum likelihood. It can do the tree search and infer support statistics for the tree at the same time

```
iqtree -m GTR+G -bb 1000 -s ccsA-ndhD.fasta
figtree ccsA-ndhD.fasta.contree
```

Let's clean a bit our folder before the next step:

```
rm *.fasta.*
```

Now that we have inferred one tree, we can estimate a tree for every single region provided. we can use a loop:

Let's try a simple loop that just print the files we want to analyze:

```
for file in *.fasta; do echo $file; done
```

We can go one step further and print the commands we want to utilize:

```
for file in *.fasta; do echo iqtree -m GTR+G -bb 1000 -s $file; done
```

This looks pretty good, now write the loop in a way it will analyze every single alignment:

```
for file in *.fasta; do iqtree -m GTR+G -bb 1000 -s $file; done
```

Explore the trees obtanined, do they represent the same relationships?

> Change your flag to green if you are good to continue ![](img/green.jpeg)

### Runing a supermatrix analysis

> Add the yellow flag to the right corner of your screen ![](img/yellow.jpeg)

All the DNA regions in this exercise belong to the chloroplast genome. Because this region is a single and large piece of DNA that does not perform recombination it is safe to assume that a single tree underlies the history of all the chloroplast. IN case like shits one it is best to concatenate all genes in a supermatrix that contains all the phylogenetic signal in a single analysis.

first we need to create a supermatrix using a python3 script that concatenates all the files and creates a partition model. Alternatively you can use [Mesquite](https://www.mesquiteproject.org/Managing%20Molecular%20Data.html#concatMatrices) a program with a graphic interface to perform the concatenation(the use of Mesquite is only advisable when the number of aligments is 5 or less)

```
python3 concatenate_all_fasta.py
```

Let's check the output files

```
aliview supermatrix.fasta
cat supermatrix.model
```

We now can run the supermatrix analysis:

```
iqtree -m GTR+G -bb 1000 -s supermatrix.fasta -spp supermatrix.model 
```

> Change your flag to green if you are good to continue ![](img/green.jpeg)

### Exercise

Create a loop that that prints the first line for every DNA alignment in today's folder. The output of the printing should look like this:

```
>Barringtonia_edulis
>Barringtonia_edulis
>Barringtonia_edulis
>Barringtonia_edulis
>Barringtonia_edulis
>Barringtonia_edulis
>Barringtonia_edulis
>Barringtonia_edulis
>Barringtonia_edulis
>Barringtonia_edulis
```

Submit your answer in CANVAS
