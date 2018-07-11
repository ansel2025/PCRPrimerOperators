# PCRPrimerOperators
## PCRPrimerVerifier
### Basic
Shows the enclosed transcripts by user-provided primer pairs. To run to program

> java -jar PrimersToTranscripts.jar 

This package requires four parameters.
Usage: java -jar PrimersToTranscripts genome.fa anno.gtf primer_5F primer_3R

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
ftp://ftp.ensembl.org/pub/release-92/fasta/
ftp://ftp.ensembl.org/pub/release-92/gtf/

Different species can be downloaded and used for reference.

Or here are two files for human. Both of them are needed.
ftp://ftp.ensembl.org/pub/release-92/fasta/homo_sapiens/dna/Homo_sapiens.GRCh38.dna.primary_assembly.fa.gz
ftp://ftp.ensembl.org/pub/release-92/gtf/homo_sapiens/Homo_sapiens.GRCh38.92.gtf.gz

We only tested on GRCh38 and haven't tried on GRCh37.

> java -Xmx10g -jar PrimersToTranscripts.jar data/Homo_sapiens.GRCh38.82.dna.primary_assembly.fa.gz data/Homo_sapiens.GRCh38.82.gtf.gz GTTCCCTGATGATCAGACTCAG CAGTCTGCAACTTATCTGTGGGCC

\>ENST00000361924        GOLGA4-001      37355133-37366240(279)
GTTCCCTGATGATCAGACTCAGAAAATTTTGGAAAGAGAAGATGCTCGGCTGATGTTTACTTCACCTCGCAGTGGTATCTTCTGAGTAAACCATCAGTCTGTGCTTAGTTAACATGTGTCATGGCTCCGATCTTCATCTTGAAGAAGAGTGACATTGGGTGACTGCTGCTTGGAAAACTGTCCACACTTGCTACTCTTTGAGAATGAAGTTGTCATTCAGGGCCCCTCATGTAGCCAAAAGACCAAGAAAAATCTGGCCCACAGATAAGTTGCAGACTG

\>ENST00000437131        GOLGA4-005      37355133-37366240(216)
GTTCCCTGATGATCAGACTCAGAAAATTTTGGAAAGAGAAGATGCTCGGCTGATGTCATGGCTCCGATCTTCATCTTGAAGAAGAGTGACATTGGGTGACTGCTGCTTGGAAAACTGTCCACACTTGCTACTCTTTGAGAATGAAGTTGTCATTCAGGGCCCCTCATGTAGCCAAAAGACCAAGAAAAATCTGGCCCACAGATAAGTTGCAGACTG

\>ENST00000356847        GOLGA4-006      37355133-37366240(216)
GTTCCCTGATGATCAGACTCAGAAAATTTTGGAAAGAGAAGATGCTCGGCTGATGTCATGGCTCCGATCTTCATCTTGAAGAAGAGTGACATTGGGTGACTGCTGCTTGGAAAACTGTCCACACTTGCTACTCTTTGAGAATGAAGTTGTCATTCAGGGCCCCTCATGTAGCCAAAAGACCAAGAAAAATCTGGCCCACAGATAAGTTGCAGACTG

The results are in the fasta format that with the overlapped isoforms and the enclosed sequences including both sides of primers.
In this example, three isoforms, 001, 005 and 006 of GOLGA4 has been found that will be amplified using the given primers. Their ensembl ids im the provided gtf file are ENST00000361924, ENST00000356847, and ENST00000356847.
The location of primers on genome coordintes is at chromosome 3 from 37355133-37366240 (strandless) and the lengths of the flanking region are either 279 bps 216 bps.


## PCRPrimerSearcher
Updating

