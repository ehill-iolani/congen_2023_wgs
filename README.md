# Congen_2023 WGS Instructions

Use these instructions to perform a genome assembly using a sample dataset of your genome.

First you are going to open a terminal on the laptop. Go to the search bar in the bottom left and type "terminal" and open the application called terminal.

Once you are in the terminal, execute the following code to get into the docker container:
```
docker exec -it genome_demo bash
```

Navigate to the data:
```
cd /home/data/
```

Check to see if your files the barcode0x directories have the .gz ending. 
```
ls barcode*/
```

If they do you will need to run the following code:
```
gunzip barcode*/*.gz
```

Once the files are uncompressed run the following command to combine them all into 1 file. Choose the command that matches your group's genome:
```
cat barcode*/*.fastq > BIC40_sample.fastq
cat barcode*/*.fastq > BIC9C_sample.fastq
cat barcode*/*.fastq > K61_sample.fastq
cat barcode*/*.fastq > BIC1A_sample.fastq
```

Now that you have combined the reads into 1 file, you can begin the ulana pipeline. Choose the command that matches your group's genome:
```
ulana -q 8 -l 1000 -c 4 -i BIC40_sample.fastq -b r941_min_fast_g507
ulana -q 8 -l 1000 -c 4 -i BIC9C_sample.fastq -b r941_min_fast_g507
ulana -q 8 -l 1000 -c 4 -i K61_sample.fastq -b r941_min_fast_g507
ulana -q 9 -l 1000 -c 4 -i BIC1A_sample.fastq -b r941_min_hac_g507
```

IMPORTANT: The Ropro analysis might take a little while, to get around this when it gets to this part hit "Ctrl + c" to cancel the pipeline and rerun the command above. It will extract the 16S gene and you can BLAST it manually yourself.

