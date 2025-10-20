# Hand-in 2 - Selection using dN/dS

In this hand-in you will analyse some data and test for selection (Part 1) and you will also solve the theoretical exercises of the Nielsen and Slatkin's Book, Chapter 9 (Part 2). For Part 1 you can choose one out of two options: 

Option A. You will analyse the [NORK](https://www.uniprot.org/uniprot/Q8LKZ1) data set for selection using the phylogenetic concepts and tools. Then you will have to answer some questions (below). Make sure to include detailed information on how the analysis were performed (for example, which substitution model was used, number of bootstraps, and so on). Example on how to calculate DN/DS in mega [Exercise](https://github.com/Jilong-Jerome/Evolutionary_Thinking_2022/tree/main/week41/Friday)

Option B. You can formulate a hypothesis about selection (look below for examples), test your hypothesis and coment your results. 

You must write a report spanning both Part 1 (either A or B) and Part 2. For Part 2 you must comment the result or show your work (the calculations to get the results). If the final result is the only thing provided, you will have failed Part 2. This report must be uploaded on Brightspace in **PDF** format before . (A single report needs to be handed in per group).

## Part 1

## Option A. Molecular phylogenetics of the Medicago genus and patterns of molecular evolution of the NORK protein

### Background for the study

Legumes have the ability to form symbiotic associations with soil bacteria (a polyphyletic group of bacteria called rhizobia) and thereby use atmospheric N2 as a source of nitrogen. Here we focus on the phylogeny of the plant genus Medicago and on a particular gene in the bacterial symbiotic recognition pathway; the NORK gene. The gene NORK (Nodulation Receptor Kinase) is required to recognize a complex sugar molecule synthesized by microbial rhizobia and start the symbiosis relationship. The C-terminal region of the extracellular contains three Leucine-Rich Repeats (LRRs) which are motifs involved in ligand binding.

### Data

The alignment of a fragment of the NORK coding sequence (CDS) gene of 32 species of the Medicago genus and 6 other species within the Legumes family is provided in MEGA format ([nork.meg.zip](nork.meg.zip)).

Additionally, a phylogeny (Fig 1) of the genus Medicago (available as a newick tree file [bena.nwk.zip](bena.nwk.zip) that can be viewed in MEGA) is provided. This phylogeny is described fully in:
Béna G et al, (Molecular phylogeny supports the morphologically based taxonomic transfer of the medicagoid Trigonella species into the genus Medicago L., Plant Syst Evol 2001, 229:217-236

<img src="Fig1.png" width="75%">

>**Fig 1.** independent phylogeny of Medicago genus (based on ITS sequences) and evolutionary transition in symbiotic specificity along the phylogeny. Topology is contained in the newick tree file [bena.nwk.zip](bena.nwk.zip). Ancestral reconstruction was used to infer the symbiotic specificities of each node. Branches where a shift in symbiotic specificity occurred are marked (numbered 1 to 5). See for details:
>Béna G, et al : Medicago – Sinorhizobium symbiotic specificity evolution and the geographic expansion of Medicago. J Evol Biol 2005, 18:1547-1558

### 1. Building a phylogeny of the Medicago genus using NORK

1.1. Which substitution model fits the data the best among JC, K2 and Tamura Nei? Why is that? Do you need to account for other parameters (R, I, Gamma,…)?

1.2. Build a phylogenetic tree using the NJ algorithm and comment on it by answer the following questions:

- Is the Medicago genus monophyletic under your phylogenetic reconstruction? 

Hint: you can easily visualize different groups in your tree by using the option in “Data/Select Taxa" and Groups” before doing the tree reconstruction. Note that Medicago samples are named by the specific name (starting with a lowercase letter) and the rest by the generic name (starting with an uppercase letter).

- Do you see major changes compared to Fig 1?

- Is there any node that has little support by bootstrap? 

### 2. Test of evolutionary hypotheses regarding the evolution of NORK in the Medicago genus

2.1. What is the average level of selective constraint (as measured by the ratio dN/dS) experienced by NORK? Discuss the estimate of dN/dS you obtain and whether it suggests purifying selection, neutrality or the occurrence of positive selection. Give the Z-score and associated p-value for the dN/dS .

2.2. Is the level of selective constraint (dN/dS) homogeneous in the Medicago phylogeny? Compare the average dN/dS estimated above with the dN/dS you can estimate in sub groups of the tree. Use the known transitions in symbiotic specificity evolution in the Medicago genus (Fig 1) to investigate whether the selective constraint has changed in specific groups of the Medicago phylogeny. Give the Z-score and associated p-value for each dN/dS ratio.

Hint: use MEGA to define subgroups in the datasets with each subgroup containing the sequences from the clade you want to examine for dN/dS and compute a mean dN/dS within those subgroups.

2.3. Do you conclude that this gene has been under positive selection, negative selection or neutrality? If there were parts of the gene positively selected, would you expect to see that signal with the tests performed? How could you test for that?

## Option B. Test your selection hypotesis

Start by formulating an hypotesis that you can test about selection. Some examples can be:

- Is SARS-CoV2 evolving neutraly? Is it under adaptive evolution? 
- Are there certain proteins in SARS-CoV2 under negative selection (structural proteins) but others under adaptive evolutions (spike protein)?
- Are pseudogenes evolving more neutraly than their functional paralogs?
- Are proteins that are highly expressed under more negative selection than proteins that are not so expressed?
- LCT (lactase) gene is an example of positive selection in Humans since certain mutations allow adult humans to digest lactose compared to other mammals. Can I identify which region of the protein is under positive selection?
- Is there more selection in introns than in exons?

You can be creative and make your own hypotesis. An aspect you need to consider is the data that you are going to use and if it is accessible to you. 

Then, you have to decide which statistic is more adequate for your hypotesis. You can use the statistics introduced to you in Chapter 9 in Nielsen and Sltakin's book:

1. dN/dS test
2. HKA test 
3. McDonald-Kreitman test
4. Tajima's D test

You should explain why you choose that statistic, what it is measuring, and what you expect the result to be. 

Then you must perform your analysis and present the results and your conclusions. Best case scenario will be that your alternative hypotesis might be correct and you find some signals of selection, but if you get that the boring null hypotesis is the most likely one... well... you will learn that science is not easy (Fig 2). 


<img src="Fig2.png" width="25%">

>**Fig 2.** Science... sometimes is hard :)


## Part 2. Solve Chapter 9 exercises from Nielsen and Slatkin book
