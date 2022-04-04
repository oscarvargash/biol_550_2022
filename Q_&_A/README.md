# Questions and Answerns 

The aim of this section is to provide answers to questions that rose over the development of student's projects. This page expected to increase in size over time. If your question is not answered here please email your instructor.

## Q: We are trying to download our sequences from GenBank onto the Linux machine, however when we download the second sequence, it completely replaces the first sequence because it downloads with the same file name: `sequence.fasta`. How do we download multiple sequences without the newest one replacing the old one?

A: You can change the name of the first sequence in your computer so the second one does not replace the first. Additionally, in GenBank, you can select several sequences and download all of them together as a single fasta file

## Q: We have all our sequences in independent `fasta` files. how do we bundle multiple sequences into the same file (so we can see it in a single `aliview` window)?

A: If you have different fasta files, for example:

```
sp1.fasta
sp3.fasta
sp4.fasta
```

You can put all of them in the same file using cat:
```
cat  sp1.fasta sp3.fasta sp4.fasta > allsp.cat
```

You can also concatenate all the fasta files in a given folder using a wild card:

```
cat  *.fasta > allsp.cat
```

## We have our data uploaded to github as a `.txt` file, is that ok?

A text file is fine, if it is in fasta format then the extension should be `.fas` or `.fasta`, so programs like `aliview` can open them immediately. Remember that the first two lines of a fasta file look like this:

```
>sequence_name
atgtagtagtagatagatgctgatcgt
```




