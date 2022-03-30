My important paragraph.
{: .alert .alert-info}
</div>

# Microbial marker gene reference database for wastewater

<b>Lou LaMartina, Angie Schmoldt, Ryan Newton</b>

Full-length 16S rRNA gene sequences, from 27F to 1492R and regions V1-V9. DNA sequences from the PacBio Sequel II were curated with DADA2, mothur, and Silva v.138. Sample information, FASTA sequences, counts, and taxonomy are publicly available in multiple formats.

## ASV files

Amplicon sequence variants (ASVs), or unique DNA sequences, of 16S ribosomal RNA genes from wastewater bacteria. <b>Counts</b> files are the number of times (reads) that ASVs occur in each sample. <b>Taxonomy</b> files show the taxonomic classification of ASVs from Kingdom to Species. ASV names range from ASV0001 to ASV1041, ranked from most to least abundant. <b>FASTA</b> sequences of ASVs whose headers include ASV ID, taxonomic assignments, read count, and read direction (R1/R2). 


> Counts: [GitHub](https://raw.githubusercontent.com/loulanomics/Full16S_sewageDatabase/main/Files/Wastewater_full16S_ASV_counts.csv)
> or [Google](https://docs.google.com/spreadsheets/d/e/2PACX-1vTyp4rmGshqL2rbSOrIGSX4R5yc4fFnRKWniIyQEWR2ctvAH1GGQBieDC2Q0eNRC71Iuhe4xqzEyudV/pubhtml)
> 
> Taxonomy: [GitHub](https://raw.githubusercontent.com/loulanomics/Full16S_sewageDatabase/main/Files/Wastewater_full16S_ASV_taxonomy.csv) or [Google](https://docs.google.com/spreadsheets/d/e/2PACX-1vQswVBHTgnHT4TuAjXktpaToTw4nwj0AeAcoXvOwPjjtrav-YhjhmTi_TI9tjosEQqYrsJcPXqjB9QW/pubhtml)
> 
> FASTA: [GitHub](https://github.com/loulanomics/Full16S_sewageDatabase/raw/main/Files/Full16S_sewageDatabase_ASV.fasta.gz)


## OTU files

Operational taxonomic units (OTUs) were generated by grouping ASVs that were at least 99.5% similar. OTU names range from OTU001 to OTU681, ranked from most to least abundant. If there was no consensus in taxonomy among ASVs within an OTU, the proportion of reads belonging to that ASV is in its name. For example, OTU011 was 16 ASVs all in the genus <i>Acidovorax</i>, but they were mixed with <i>defluvii</i> (11), <i>carolinensis</i> (4), or were unclassified (1) to species. Among all the reads in OTU011 (5568), 67% (3719) were assigned to <i>defluvii</i>, while <i>carolinensis</i> and unclassified were 16% and 17%, respectively. Therefore, the OTU names are OTU011_67, OTU011_17, and OTU011_16.

> Counts: [GitHub](https://raw.githubusercontent.com/loulanomics/Full16S_sewageDatabase/main/Files/Wastewater_full16S_OTU_counts.csv)
> and [Google](https://docs.google.com/spreadsheets/d/e/2PACX-1vS9mQT7KdVK1w0AmtZjgIwjfIkQPC74ESsye7QUznNiGS2aGDgNnleKgw7BT8_mFacP4sc-TgYkmELB/pubhtml)
> 
> Taxonomy: [GitHub](https://raw.githubusercontent.com/loulanomics/Full16S_sewageDatabase/main/Files/Wastewater_full16S_OTU_taxonomy.csv) and [Google](https://docs.google.com/spreadsheets/d/e/2PACX-1vSqziz00qo4pZRUTKs9p0XC6j-vV8j2ctQt50WuFDrI2tfnNYQHfP3XYUbwF9nj5swNdYDQs45bJbYb/pubhtml)


## R Data and code

[Phyloseq](https://joey711.github.io/phyloseq/) R object with ASV or OTU counts, taxonomy, and sample information combined, for easy exploration in R. If you want to recreate the analysis, output files from each step (code script) are included.

> Phyloseq: [ASV](https://github.com/loulanomics/Full16S_sewageDatabase/raw/main/RData/Wastewater_full16S_ASV_phyloseq.RData) and [OTU](https://github.com/loulanomics/Full16S_sewageDatabase/raw/main/RData/Wastewater_full16S_OTU_phyloseq.RData)
> 
> trim residual primers: 
> [code](https://github.com/loulanomics/Full16S_sewageDatabase/blob/main/Code/01_full16S_removePrimers.R), 
> [input](https://raw.githubusercontent.com/loulanomics/Full16S_sewageDatabase/main/RData/Full16S_assignTaxonomy_addSpecies.txt) & 
> [input](https://raw.githubusercontent.com/loulanomics/Full16S_sewageDatabase/main/RData/Full16S_dada2_sequencetable.txt)
> 
> dereplicate trimmed reads: 
> [code](https://github.com/loulanomics/Full16S_sewageDatabase/blob/main/Code/02_full16S_derepSeqs.R), 
> [input](https://raw.githubusercontent.com/loulanomics/Full16S_sewageDatabase/main/RData/01_counts.csv) &
> [input](https://raw.githubusercontent.com/loulanomics/Full16S_sewageDatabase/main/RData/01_taxa.csv)
> 
> subset sewage samples:
> [code](https://github.com/loulanomics/Full16S_sewageDatabase/blob/main/Code/03_full16S_subSewage.R), 
> [input](https://raw.githubusercontent.com/loulanomics/Full16S_sewageDatabase/main/RData/02_counts.csv) &
> [input](https://raw.githubusercontent.com/loulanomics/Full16S_sewageDatabase/main/RData/02_taxa.csv)
> 
> cluster ASVs to OTUs:
> [code](https://github.com/loulanomics/Full16S_sewageDatabase/blob/main/Code/04_full16S_clusterASV.R), 
> [input](https://raw.githubusercontent.com/loulanomics/Full16S_sewageDatabase/main/RData/03_counts.csv) &
> [input](https://raw.githubusercontent.com/loulanomics/Full16S_sewageDatabase/main/RData/03_taxa.csv)
> 
> assess taxonomy:
> [code](https://github.com/loulanomics/Full16S_sewageDatabase/blob/main/Code/05_full16S_taxAssess.R), 
> [input](https://raw.githubusercontent.com/loulanomics/Full16S_sewageDatabase/main/RData/04_counts.csv) &
> [input](https://raw.githubusercontent.com/loulanomics/Full16S_sewageDatabase/main/RData/04_taxa.csv)
> 

## Sample set

In total, 46 wastewater treatment plant influent (raw sewage) underwent 16S rRNA gene sequencing. Samples encompass a wide range of bacterial diversity over space and time, according to previous studies ([1](https://microbiomejournal.biomedcentral.com/articles/10.1186/s40168-021-01038-5), [2](https://microbiomejournal.biomedcentral.com/articles/10.1186/s40168-021-01038-5)). <b>Temporally</b>, 24 sewage samples were collected once a month for two years from a single treatment plant. <b>Spatially</b>, 22 treatment plants were sampled from across the US, with southern samples from summer and northern samples from winter.

> [GitHub](https://github.com/loulanomics/Full16S_sewageDatabase/blob/main/Files/Wastewater_full16S_sample_metadata.csv) and [Google](https://docs.google.com/spreadsheets/d/e/2PACX-1vQ1Tv35bihJrfe7DFr_385SqhoLBcokX3LrqCIgKJL26hxhFv1cYT9dhH-pXuO8w9ugc9ve5k2eyPB0/pubhtml)

## Analysis

1. <b>Marker gene.</b>  Hypervariable and conserved regions (V1-V9) were PCR-amplified at [27F and 1492R](https://academic.oup.com/nar/article/47/18/e103/5527971). Unique [barcodes](https://github.com/PacificBiosciences/Bioinformatics-Training/blob/master/barcoding/pacbio_384_barcodes.fasta) were appended to primers to allow  sequencing of all samples simultaneously (multiplex).

2. <b>DNA sequencing.</b>  PCR amplicons were sequenced in multiplex on a PacBio Sequel II.

3. <b>Data processing.</b>  Data files were subsetted to individual samples according to their assigned barcodes. Cutadapt was used to trim primers and barcodes from reads, [DADA2](https://benjjneb.github.io/dada2/tutorial.html) generated ASV counts and assigned taxonomy, and [mothur](https://mothur.org/wiki/cluster/) clustered ASVs into OTUs.
