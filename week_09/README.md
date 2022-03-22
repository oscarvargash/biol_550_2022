# Week nine: creating scripts; calibrating a phylogeny

> Add the yellow flag to the right corner of your screen ![](img/yellow.jpeg)

To start this tutorial you need to be logged in the Linux virtual machine
[vlinux.humboldt.edu](https://vlinux.humboldt.edu/)

Once logged in the Linux machine, look for the Terminal, it is an icon that contains the characters `>\_`

You can also write `terminal` in the search bar of the main manu located in the left bottom of the operating system.

### Creating a script to get our files ready for analysis

One of the advantages of using the command line is that you can save your commands into a text file for a later re-execution. We will write a small script to get our computer ready for toaday's exercise:

1. Create a new text file using nano:
```
nano week9.sh
```
The `.sh` suffix indicates that this script is to be excuted on shell (which is the terminal of Linux)

2. Add ALL the commands to be used in your script, copy and paste the text below into nano:

```
# quick sript to get ready for the lab of week 9
cd Documents
mkdir week_09
cd week_09
wget https://github.com/oscarvargash/biol_550_2022/raw/main/week_09/files/files.zip
unzip files.zip

```
Notice how there is an "enter" at the end of the sript, this is to ensure the last line is executed by the shell. Also notice that lines that start with `#` are not interpreted as commands, these are comments that you can add to your script to expmain it.

3. Save the file while closing nano:
<kbd>control</kbd> + <kbd>x</kbd>

Then answer:
<kbd>y</kbd>

Finally press:
<kbd>return</kbd>

4. Execute the script
```
./week9.sh
```











Download and unzip data from this lab:

```
wget https://github.com/oscarvargash/biol_550_2022/raw/main/week_08/files/files.zip
unzip files.zip
```

### Preparing the file for MrBayes

Mr.Bayes only works with `nexus` files. Therefore, we need to comvert our `fasta` file into a a `nexus` one. We have done this before with `Aliview`:

```
aliview cp_2_genes.fasta
cat cp_2_genes.model
```

In `aliview`:

1. click on the `file` menu
2. `save as` nexus (for Mr. bayes, second nexus option)
3. `save`

MrBayes operates like PAUP, it is a command line program that can operate interactively or with a script. We will use a script today. In order to do so, we need to add the commands for our analysis to the end of our fasta file:

```
xdg-open cp_2_genes.nexus
xdg-open cp_2_genes.model
```

Once the file is open, paste the following text at the bottom of the `nexus` file after removing the block for codons

```
begin mrbayes;

    [This block defines several different character sets that could be used in partitioning these data
    and then defines and enforces a partition called favored.]

    charset ccsA-ndhD = 1-1263;
    charset ycf1and2 = 1264-3709;

    partition favored = 2: ccsA-ndhD, ycf1and2;

    set partition=favored;
    lset app=(1,2) rates=gamma nst=6;
    unlink revmat=(all) shape=(all) statefreq=(all);
    prset applyto=(all) ratepr=variable;
    
    mcmc ngen=1000000 printfreq=1000 samplefreq=1000 relburnin=yes burninfrac=0.25							
	diagnfreq=1000 diagnstat=maxstddev											
	nchains=4 savebrlens=yes 
	filename=cp_2_genes;
	sump;
	sumt;

end;

```

### Running MrBayes

```
mb -i cp_2_genes.nexus
```

This will take some minutes, lets keep the program running while we talk about all the parameters used in this analysis. Once the analysis has finished type `quit` to exit MrBayes

> Change your flag to green if you are good to continue ![](img/green.jpeg)

### Checking the output

> Add the yellow flag to the right corner of your screen ![](img/yellow.jpeg)

Let's take a peek of some of these files

```
head cp_2_genes.run1.p
head cp_2_genes.run1.t
```

What are those files?

We can take a more detailed look at the `*.p` file:

```
tracer
```

Drag and drop the one of the `*.p` files on the  `tracer` application. Summary statistics are shown for every parameter calculated.

Now drop the other `*.p` file. If both chains converged they should presetn similar likelihood values.

If everything looks good, now you know that you can trust the final result:

```
figtree cp_2_genes.con.tre
```

You will need to turn on the `node labels` and select the appropiate statistic.

Congrats you have performed your first Bayesian phylogenetic analysis,

> Change your flag to green if you are good to continue ![](img/green.jpeg)


### Exercises

## 1

Do a Maximum Likelihood analysis of `cp_2_genes.fasta` along with `cp_2_genes.model`, make sure every gene has a different partition. Compare the Maximum Likelihood tree against the Bayesian tree and answer the following questions:

1. In terms of relationships among the tips. Do both trees have the same relationships? Give specific examples to support your answer.

2. In terms of branch lenghts. Do both trees show similar branch lengths? Give specific examples to support your answer.

3. In terms of support. Do both trees present similar support values? Give specific examples to support your answer and remember that roughly 70% bootstrap corerspond to 0.95 posterior probability.

Submit your answers to CANVAS

## 2

Create a loop that that prints the first line for every DNA alignment in used in week's 7 exercise (iqtree tutorial). The output of the printing should look like this:

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

Submit your loop to CANVAS
