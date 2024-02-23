# MyGenome

## 1. Analysis of Sequence Quality
The F1 and R1 sequence datasets were analyzed using FASTQC:
```bash
ssh -Y jama251@jama251.cs.uky.edu
cd MyGenome
fastqc &
```
Load F1 and R1 datasets into GUI interface.
Take screen shots of output files:
![F1screenshot.png](/data/F1_FastQC_SS.png)
![R2screenshot.png](/data/R1_FastQC_SS.png)

## Ran Trimmomatic
```bash
java -jar Trimmomatic-38.jar PE -threads 16 -phred33 -trimlog file.txt UFVPY
ILLUMINACLIP:adaptors.fasta:2:30:10 SLIDINGWINDOW:20:20 MINLEN:100
```

## 3. Count the number of forward reads remaining
```bash
grep -v "@" UFVPY204_1_paired.fastq | grep -v "+" | grep -v "F" | wc -c
```
 I wanted to verify that there were no extra characters being counted so I ran the following code.
```bash
grep -v "@" UFVPY204_2_paired.fastq | grep -v "+" | grep -v "F" | grep -v "A" | grep -v "T" | grep -v "C" | grep -v "G"| wc -c
```
It came back with a count of zero.
