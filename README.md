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
![F1screenshot.png](/data/F1screenshot.png)

## Ran Trimmomatic
```bash
java -jar...
```

## 3. Count number of forward reads remaining
```bash
grep -v "@" UFVPY204_1_paired.fastq | grep -v "+" | grep -v "F" | wc -c
```
Verified that there were no extra characters being counted so I ran the following code and it came back with a value of 0
```bash
grep -v "@" UFVPY204_2_paired.fastq | grep -v "+" | grep -v "F" | grep -v "A" | grep -v "T" | grep -v "C" | grep -v "G"| wc -c
```
