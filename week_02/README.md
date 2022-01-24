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
```

We can try to get peek in the in the file to see what it is about. Print to the screen the first ten lines of the file by typing using the command `head`:

```
head Diplostephium_azureum_R1_nrmap.fastq.gz
```

What did you see?

It turns out that this is also a compressed file. `*.gz` is a common tupe of compression in sequencing. Most bioiformatic programs can work with `*.gz` files, saving space in hard drives. We can look at the file without decompressing it by:

```
zcat Diplostephium_azureum_R1_nrmap.fastq.gz | head
```

As you can see we are "piping" or passing with `|` the uncompressed text to `head`, which prints only the first ten lines of the file

What is this file?

We can use FastQC to evaluate the quality of the file. First should figure out how does FastQC works. Most programs have a help menu.

```
~/../../opt/FastQC/fastqc -help
``` 

It seems that we can simply add the name of the file as as the first argument, and we shouls add `-o` (output) to specify where the program should write the report

```
~/../../opt/FastQC/fastqc Diplostephium_azureum_R1_nrmap.fastq.gz -o .
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


