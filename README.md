# scraping_atypical
NCBI assembly data reports can be scraped for "atypical" assemblies. 
This is a good while read line base script that can be eddited based on command a file requirements

```
#!/bin/bash
counter=0
while read line;
do
counter=$((counter+1))
test=$(echo $line | sed 's|\(.*\)_.*|\1|' );
wget -q https://api.ncbi.nlm.nih.gov/datasets/v1/genome/accession/${test}/download
unzip -q download
isAtypical=$(grep -c isAtypical ./ncbi_dataset/data/assembly_data_report.jsonl)
echo $line $isAtypical >> scraping_atypical_assemblies.txt
rm download 
rm -r ncbi_dataset
rm README.md
echo $counter
done < curated_database
#done
```

Atypical assemblies can then be removed from the curated_database using 
```
xarg rm <[filename].txt
```
