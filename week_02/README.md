# Week two

> Add the yellow flag to the right corner of your laptop ![](img/yellow.jpeg)

To start this tutorial you need to be logged in the Linux virtual machine
[vlinux.humboldt.edu](https://vlinux.humboldt.edu/)

Once logged in the Linux machine, look for the Terminal, it is an icon that contains the characters '>\_'

You can also write 'terminal' in the search bar of the main manu located in the left bottom of the operating system.

## Using programs

The terminal is a powerful to run programs, as you can analyze tons of data with only a single command. In this tutorial we will run several aplpications in the terminal and will learn the principles of automatizing data processing.

### Looking at the quality of a file that contains DNA sequences obtanied using high-throughput-sequecing (also known as next-generation-sequencing)

We will use FastQC quatify measure the quality of data in a file.
Please dowload in your machine the two files by typing:

```
cd Documents
mkdir week_02
cd week_02
wget https://github.com/oscarvargash/biol_550_2022/raw/main/week_02/files/reads1.zip
```

As you can see, this is a compressed file. We can decompressed by

```
unzip reads1.zip
ls
```

We see that there are some extra files there that are probably inherited from compressing these files in a Mac machine. How can we remove these files from our folder? (tio you need to lookat the cheat sheet)

<details>
  <summary>Click to see an answer!</summary>
  
```
rm -r *MAC*
```

</details>


We can try to get peek in the in the file to see what it is about. Print to the screen the first ten lines of the file by typing using the command `head`:

```
head Diplostephium_azureum_R1_nrmap.fastq.gz
```

What did you see?

It turns out that this is also a compressed file. `*.gz` is a common type of compression use in DNA analysis. Most bioinformatic programs can work with `*.gz` files, saving space in hard drives. We can look at the file without decompressing it by:

```
zcat Diplostephium_azureum_R1_nrmap.fastq.gz | head
```

As you can see we are "piping" or passing with `|` the uncompressed text to `head`, which prints only the first ten lines of the file

What is this file?

We can use FastQC to evaluate the quality of the file. First should figure out how does FastQC works. Most programs have a help menu.

```
fastqc -help
``` 

It seems that we can simply add the name of the file as as the first argument, and we shouls add `-o` (output) to specify where the program should write the report

```
fastqc Diplostephium_azureum_R1_nrmap.fastq.gz -o .
``` 

Once it has finish you can list all files and see the output.

```
ls
```

You can navigate with the mouse and open the report in html

Congrats!!! you have excuted a program succesfully

> Change your flag to green if you are good to continue ![](img/green.jpeg)

### Exercise 1

Analyze the second file with FastQC. Upon completion of the analysis compare the results and decide which of the files contains reads with better quality. Submit your answer in CANVAS along with a brief explanation.

### Triming and cleaning reads

Slide show aboout next-generation sequencing.

We will trim the reads found in the files from contaminants and low quality regions. We sill a suite of programs called bbtools, specifically we will use the program `bbduk.sh`. Let's call the program and see the help:

```
bbduk.sh -h
```

It seems that with bbduk.sh `-h` does not work. Let's follow the screen instruction and type

```
bbduk.sh
```

We want to trim contamintants found in the reference file 'illumina_primers.fasta' 

```
bbduk.sh in=Diplostephium_azureum_R1_nrmap.fastq.gz ref=~/../../opt/bbmap/resources/adapters.fa ktrim=r k=21 mink=11 hdist=2 ml=50 out=Diplostephium_azureum_R1_nrmap.f.fastq.gz stats=stats1.txt
```

`ktrim` indicates which side of the read should be trimmed
`k` indicates the kamer size to look for contaminats, contaminants shorther than K will not be found
`mink` looks for shorter kmers at the end of reads
`hdist` indicates the number of mistmatches allowed in the kamer for matching to contaminants
`ml` is the minimum lenght of a given read


> Add the yellow flag to the right corner of your laptop ![](img/yellow.jpeg)


### Exercise 2

Perform the filtering of the second file and perform a quality control on the filtered files. Answer the following questions:

1. Which file had more contaminants?
2. Was there a significant difference between the filtered and non-filtered reports by fastqc


<details>
  <summary>Click here to see the commands to analyze the data of exercise 2, click here only as your last resource</summary>
  
```
bbduk.sh in=Diplostephium_azureum_R2_nrmap.fastq.gz ref=~/../../opt/bbmap/resources/adapters.fa ktrim=r k=21 mink=11 hdist=2 ml=50 out=Diplostephium_azureum_R2_nrmap.f.fastq.gz stats=stats2.txt
fastqc Diplostephium_azureum_R1_nrmap.f.fastq.gz -o .
fastqc Diplostephium_azureum_R2_nrmap.f.fastq.gz -o .
```

</details>





