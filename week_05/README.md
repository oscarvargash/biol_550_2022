# Week five: building trees using PAUP, git

> Add the yellow flag to the right corner of your screen ![](img/yellow.jpeg)

To start this tutorial you need to be logged in the Linux virtual machine
[vlinux.humboldt.edu](https://vlinux.humboldt.edu/)

Once logged in the Linux machine, look for the Terminal, it is an icon that contains the characters `>\_`

You can also write `terminal` in the search bar of the main manu located in the left bottom of the operating system.

### Download data

Make a folder for this week:

```
cd Documents
mkdir week_05
cd week_05
```

Download data from this lab:

```
wget https://github.com/oscarvargash/biol_550_2022/raw/main/week_05/files/supermatrix.fasta
```

### Exporting the data as a nexus file

So far we have only been working with `*.fasta` files; PAUP, however, does not read fasta files, and instead uses nexus files. We can use aliview to export our matrix to `*.nexus`

```
aliview supermatrix.fasta
```

Then do the following:
1. Click on `file`
2. Click on `save as nexus`
3. Keep the suggested name and `save`
4. Close aliview


How do we know the format has changed?

<details>
  <summary>Click to see an answer!</summary>

```
head supermatrix.nexus
```

</details>

> Change your flag to green if you are good to continue ![](img/green.jpeg)

### Using PAUP

Paup can be used as an interactive program or you can write all your commands at the end of a nexus file to perform analysis. Today we will use interactively using one command at a time. To open PAUP simply type:

> Add the yellow flag to the right corner of your screen ![](img/yellow.jpeg)

```
paup4a168_ubuntu64
```

You can see that the command line has change and now says `puap>`. You are now inside the PAUP program, and PAUP is waiting for instructions.

Let's see what are our command options:

```
?
```

In PAUP, we first need to open our data matrix:

```
execute supermatrix.nexus
```

You should see a summary of the about the taxa imported.

In order to better make sense of trees produced, we will set the outgroup:

```
outgroup Typha_latifolia
```

Do a parsimony search:

```
hsearch
```

When asked about increasing the number of maximum trees, type `y` and the type option `2` to avoid this question in the future. At the end of the search you should see a summary of all the trees found.

We can see a single tree by typing

```
ShowTrees
```

Because we have more than a 100 trees, a good strategy is to summarize our results into a concensus tree.

```
contree
```

You will realize that the consesus tree has some polytomies, these polytomies indicate inconsistensis of multiple trees that contain the same lenght.

Let's save the tree

```
contree / treefile = par_con.tre
```

Congrats, you have performed your first phylogenetic analysis!!!!!

Let's quit paup

```
quit
```

A better way to vizualize trees is to use figtree

```
~/../../opt/FigTree_v1.4.4/bin/figtree par_con.tre
```

Figtree will become your best friend.

> Change your flag to green if you are good to continue ![](img/green.jpeg)

### GitHub

GIT is a version control is a system (VCS) that records changes to a file or set of files over time so that you can recall specific versions later. 

Why a VCS? Science is about repeatability and reproducibility. Similarly to making your genetic data available to GenBank, making you code available in a repository will make your science more accessible, with the added bonus of writing code in collaboration easily.

Why Git? it is a Distributed VCS, it is more flexible and of course it is popular, and this means, more documentation and long term support in most cases. There are dozens of version control systems on the market, but some of the world's most renowned projects (like the Linux Kernel, Ruby on Rails, or jQuery) and several well known companies (Google, Facebook, Microsoft, Twitter, LinkedIn, Netflix) are using Git as their VCS of choice. 

Github and Bitbuckect are web interfaces of `git`, In the last years code-specific repositories have become popular among biologists. Github and Bitbuckect are the main platforms used. Both platforms offer a free accounts, but you can open an academic account with pro capabilities with your UCSC email.

# Creating a GitHub account

> Add the yellow flag to the right corner of your screen ![](img/yellow.jpeg)

Go to https://github.com/ and sign up / create account / register.

***NOTE:*** For Github Education (later) go [here](https://education.github.com/discount_requests/new)

> Change your flag to green if you are good to continue ![](img/green.jpeg)

# Creating a repository

> Add the yellow flag to the right corner of your screen ![](img/yellow.jpeg)

On your github homepage:

1. click on `repositories`
2. click on `new`
3. add the name `biol550`
4. select `private`
5. select `add README.md`
6. click on `create repository`

Once in your repository you can edit the `README.md` file by clicking on the pencil icon. You can preview your changes, and when you are satisfied, you can commit to those changes. You will be writing your project in github, so for now we can add a blank page that you will be writing along with the development of your project. Please copy and paste this into your README.md file.

```
# This is is the title of project

this is the first paragraph explaining the question of my project

This is the paragraph explanin the hypothesis I/we are testing

This is the paragraph explaning where the data is going to be obtained from with a preliminary plan for analysing it.
```

You can now more about the sytax of markdown github [here](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)

You can also check the raw text for the tutorials of this class.

For simplicity you will be using the on-line github platform. It is, however, possible to link github with local files; this is out of the scope for this class, but you can know more about [here]()

To make your repository accesible to Oscar, you need to:
1. Click on `settings`
2. Click on `colaborators`
3. Add `oscarvargash` as a collaborator

> Change your flag to green if you are good to continue ![](img/green.jpeg)

### Exercise

Infer, save, and compare a NeighborJoining `nj` tree against a `upgma` tree. Are these trees different?

Type your answer in the canvas exercise for this lab.