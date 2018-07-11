# PCRPrimerOperators
## PCRPrimerVerifier
### Basic
Shows the enclosed transcripts by user-provided primer pairs. To run to program

```
> java -jar PrimersToTranscripts.jar 
```

This package requires four parameters.
Usage: `java -jar PrimersToTranscripts genome.fa anno.gtf primer_5F primer_3R`

The details of the four parameters:
1. A reference genome file in FASTA format.
2. A genome annotation file, in GTF format, contains information of genes, such as their locations, region, chromosomes.
3. A five prime end PCR primer.
4. A three prime end PCR primer (on the reverse strand of the above five prime end primer).


### Examples
Find which transcripts will be amplified by 
5F: GTTCCCTGATGATCAGACTCAG
3R: CAGTCTGCAACTTATCTGTGGGCC

The genome fasta file is from Ensembl website and the gtf file is obtained from 

[ftp://ftp.ensembl.org/pub/release-92/fasta/](ftp://ftp.ensembl.org/pub/release-92/fasta/)

[ftp://ftp.ensembl.org/pub/release-92/gtf/](ftp://ftp.ensembl.org/pub/release-92/gtf/)

Different species can be downloaded and used for reference.

Or here are two files for human. Both of them are needed.

`wget ftp://ftp.ensembl.org/pub/release-92/fasta/homo_sapiens/dna/Homo_sapiens.GRCh38.dna.primary_assembly.fa.gz`

`wget ftp://ftp.ensembl.org/pub/release-92/gtf/homo_sapiens/Homo_sapiens.GRCh38.92.gtf.gz`

We only tested on GRCh38 and haven't tried on GRCh37.

```java
java -Xmx10g -jar PrimersToTranscripts.jar Homo_sapiens.GRCh38.
92.dna.primary_assembly.chr21.fa.gz Homo_sapiens.GRCh38.92.chr21.gtf.gz TGGCTCAGCGCCTGGCGGGGAATG ACCTTCAGCAGCTCGTCGTGCGTA
```

```
\>ENST00000492638        RRP1-206        +21:43789667-43791380(127)
TGGCTCAGCGCCTGGCGGGGAATGAGCAGGTGACCCGGGACCGGGCGGTGAGGAAGCTCCGGAAATACATCGTCGCCAGG
ACTCAGCGGGCCGCAGGTGGTTTTACGCACGACGAGCTGCTGAAGGT

\>ENST00000497547        RRP1-207        +21:43789667-43791380(127)
TGGCTCAGCGCCTGGCGGGGAATGAGCAGGTGACCCGGGACCGGGCGGTGAGGAAGCTCCGGAAATACATCGTCGCCAGG
ACTCAGCGGGCCGCAGGTGGTTTTACGCACGACGAGCTGCTGAAGGT

\>ENST00000483896        RRP1-205        +21:43789667-43791380(168)
TGGCTCAGCGCCTGGCGGGGAATGAGCAGGTGACCCGGGACCGGGCGGTGAGGAAGCTCCGGAAATACATCGTCGCCAGG
ACTCAGCGGGCCGCAGATTAACCTTGTGGCCACTGTCCAGCTTAGGAAACCGTCAAGGTGGTTTTACGCACGACGAGCTG
CTGAAGGT

\>ENST00000475534        RRP1-204        +21:43789667-43791380(60)
TGGCTCAGCGCCTGGCGGGGAATGAGCAGGTGGTTTTACGCACGACGAGCTGCTGAAGGT
```

The results are in the fasta format that with the overlapped isoforms and the enclosed sequences including both sides of primers.
In this example, three isoforms, 204, 205, 206 and 207 of Ribosomal RNA Processing 1 (RRP1) has been found that will be amplified using the given primers. Their ensembl ids im the provided gtf file are ENST00000492638, ENST00000497547, ENST00000483896, and ENST00000475534.
The location of primers on genome coordintes is on the positive strand at chromosome 21 from 43789667-43791380 and the lengths of the flanking region are 60 bps, 127 bps, or 168 bps.


## PCRPrimerSearcher
Updating

