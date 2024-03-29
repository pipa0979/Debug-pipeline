# FISHR2
This is the newest version of FISHR which detects IBD segments between individuals.


# FISHR2

This is the newest version of the FISHR (Find IBD Shared Haplotypes Rapidly) program. Major changes from V1:
1) Can be used with -hapsfile, -sample file, -geneticmapfile
2) Always reduced
3) no outfile or bin_out
4) use "./FISHR2 -help" command to view the list of flags and their usuage. 

To Download:
- 1. In your terminal write  
"git clone https://github.com/matthew-c-keller/FISHR2.git" to download the repository

- 2. Other way is to go to this link
"https://github.com/matthew-c-keller/FISHR2"
Click clone or download -> Download zip -> Extract zip file.

- 3. If you want to install git use:
	- For ubuntu based system:
	sudo apt-get update
	sudo apt-get install git
	- For Mac users, visit the link below and follow the instructions:
	http://mac.github.com.
	- For other operating systems, visit the following link and follow instructions:
	https://help.github.com/articles/set-up-git/


To Compile FISHR2: 
- Navigate to folder where the makefile exists and type 'make' in your command line. 
- This will create a binary file FISHR2 in the directory.
- To execute the program refer the samples below.



Note:

-  Can be used in parallel with Germline
-  Can be used with .hap, .sample,.gen files as well as .ped and .map files.

Known Issues:
See Instructions.txt
- Don't have git installed, see the "To Download" above for instructions.
- Boost libraries missing:
FIX: sudo apt-get install libboost-all-dev.
Use the commmand above to install boost in your Unix/mac system.

- If thre's a problem installing boost, there is a binary  file called 'FISHR2' already included. You needn't compile it. You can just start using it. See the Samples Below.


Extra/New features:
- To use -gen, -hap, -map files use:
 -geneticmapfile ./src/<filename>.gen -samplefile ./<filename>.sample -hapsfile ./<filename> 
- Specifying -germline_output ./newFolderHere/ with put the output generated by germline in the specified path.
- To use -ibd2
-ibd2 thresholdvalue


It will create that new folder if it doesn't exists, if folder already exists it uses the existing folder. 
Not mentioning the -germline_output, will not output any file generated by germline. 



Example:

./binaries/FISHR2 -mapfile ./src/Beagle.Phased.Group2.1k.map -pedfile ./src/Beagle.Phased.Group2.1k.ped  -bits 20 -err_hom 0 -err_het 0  -min_cm_initial 3 -homoz  -w_extend -h_extend -min_cm_final 3 -min_snp 64 -window 50 -gap 100 -output-type finalOutput -count.gap.errors TRUE -emp-pie-threshold 0.015 -ma-threshold 0.2 -log-file logs |gzip > FISHR_OUT.gz


./binaries/FISHR2 -geneticmapfile ./src/big.gens -samplefile ./src/big.sample -hapsfile ./src/big.hap   -bits 20 -err_hom 0 -err_het 0  -min_cm_initial 1.5 -homoz  -w_extend -h_extend -min_cm_final 3 -min_snp 64 -window 50 -gap 5 -output-type finalOutput -count.gap.errors TRUE -emp-pie-threshold 0.015 -ma-threshold 0.2 -log-file logs |gzip > FISHR_OUT.gz


./binaries/FISHR2  -mapfile ./src/Beagle.Phased.Group2.1k.map -pedfile ./src/Beagle.Phased.Group2.1k.ped  -bits 20 -err_hom 0 -err_het 0  -min_cm_initial 1.5 -homoz  -w_extend -h_extend -min_cm_final 3 -min_snp 64 -window 50 -gap 5 -output-type finalOutput -count.gap.errors TRUE -emp-pie-threshold 0.015 -ma-threshold 0.2 -log-file logs -germline_output ./newFolderHere/ |gzip > FISHR_OUT.gz


./binaries/FISHR2 -mapfile ./src/Beagle.Phased.Group2.1k.map -pedfile ./src/Beagle.Phased.Group2.1k.ped  -bits 20 -err_hom 0 -err_het 0  -min_cm_initial 1.5 -homoz  -w_extend -h_extend -min_cm_final 3 -min_snp 64 -window 50 -gap 5 -output-type finalOutput -count.gap.errors TRUE -emp-pie-threshold 0.015 -ma-threshold 0.2 -ibd2 2.0   -log-file  logs -germline_output ./src/TestFolder |gzip > FISHR_OUT.gz


./binaries/FISHR2 -mapfile ./src/Beagle.Phased.Group2.1k.map -pedfile ./src/Beagle.Phased.Group2.1k.ped  -bits 20 -err_hom 0 -err_het 0  -min_cm_initial 3 -homoz  -w_extend -h_extend -min_cm_final 3 -min_snp 64 -window 50 -gap 5 -output-type finalOutput -count.gap.errors TRUE -emp-pie-threshold 0.015 -ma-threshold 0.2 -ibd2 2.0   -log-file  logs -germline_output ./src/TestFolder |gzip > FISHR_OUT.gz