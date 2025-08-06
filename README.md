# scraping_atypical
NCBI assembly data reports can be scraped for "atypical" assemblies. 
This is a good while read line base script that can be eddited based on command a file requirements

To download the file assembly data report file from NCBI for each accession GCA/GCF in the curated database.  
The download will be presented as a zipped file named "ncbi_dataset", inside will be an unzipped "ncbi_dataset" folder and a "README.md" file. Click in the folder, inside it has a folder named "data", inside this is a folder named the accession number which contains the fasta file and sequence report, a file named "assembly_data_report.jsonl" and a "dataset_catalog.json"  

Path = ncbi_dataset(zipped)/ncbi_dataset/data/assembly_data_report.jsonl 

2. Move all of the reports mv *assembly_data_report.jsonl ./curated_database_genome_assemblies_data_report
   
4. Grep command on all files looking for "true" this will only be present if the genome assembly is atypical "isAtypical". Then move (mv) these files into folder "genomes_flagged_atypical"
   
6. If this is only a few then can manually check and make note of the atypical flag and manually remove from curated_database.  
If too many, then can ask to print the accession number of each one into a csv file from this can create a loop to remove the many genome assemblies. 


Atypical assemblies can then be removed from the curated_database using 
```
xarg rm <[filename].txt
```
