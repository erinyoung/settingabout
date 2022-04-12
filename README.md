# SettingAbout

The fundamental goal of SettingAbout is to find a reasonable and reproducible starting location for a closed plasmid sequence with no extra fluff. The assumption is that each sequence in a fasta or multifasta is complete and circular. SettingAbout uses blast to identify genes and rotate the start of the plasmid sequence accordingly. 

# Dependencies

- blast
- samtools

# Other tools worth noting that were used as inspiration and resources for this code include:

- [Circulator](https://sanger-pathogens.github.io/circlator/) is a useful tool for adjusting the starting position of linearized bacterial sequences. 

According to Circulator's documentation (https://github.com/sanger-pathogens/circlator/wiki):
> Any contigs that were identified as circular then have their start position changed. If a dnaA gene is found, then that is used as the starting position (or the user can provide a FASTA file of sequences to search for within the contigs). If no dnaA gene is found then prodigal is used to identify the gene nearest the centre of the contig, which is then used as the start position of the contig.

This creates a problem when circularizing plasmids in a constent manner.

- [Unicycler](https://github.com/rrwick/Unicycler) also has a module that includes circularization. Unicycler includes identification of dnaA with tblastn, as well as a few other genes. A list of fastas for searching is located in the [unicycler/gene_data directory](https://github.com/rrwick/Unicycler/tree/main/unicycler/gene_data). This list, however, still leaves many plasmids without consistent start sites.
