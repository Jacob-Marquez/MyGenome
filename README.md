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
grep -v "@" UFVPY204_1_paired.fastq | grep -v "+" | grep -v "F" | grep -v "A" | grep -v "T" | grep -v "C" | grep -v "G"| wc -c
```
It came back with a count of zero. However when using wc -c it does count the number of newline characters. In order to offset this I ran the following command to count the number of newlines.
```bash
grep -v "@" UFVPY204_1_paired.fastq | grep -v "+" | grep -v "F" | wc -l
```
Using the number this returned we can take the first number that we got including new line characters and subtract the second number we got. For the forward read I got 1,166,996,616 - 7,732,830 = 1,159,263,786 bases.

For the reverse read I got 1,116,871,878 - 7,732,830 = 1,109,139,048 bases.

Adding the two numbers together: 1,159,263,786 + 1,109,139,048 = 2,268,402,834 total bases.

