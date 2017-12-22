# SuperUsefull


# 1. Touch all files
find  -type f  -name "*" -exec touch {} +

# 2. nb of elements within folder
find . -type d -print0 | while read -d '' -r dir; do
    files=("$dir"/*)
    printf "%5d files in directory %s\n" "${#files[@]}" "$dir"
done

# 3.  Recursive grep
 find . -type f -exec grep -l "VC0860_VC0860_Hypothetical" {} +
 
# 4. Remote blast with loop
 a=0;for i in $(ls *.faa); do echo $(echo $i | cut -d'_' -f1,2,3) ;~/software/ncbi-blast-2.6.0+/bin/blastp -db nr -remote -outfmt 6 -evalue 1e-8 -show_gis -num_alignments 1 -max_hsps 20 -out BlastUniqueID/blastProt_nrREMOTE_$(echo $i | cut -d'_' -f3).xml -query $i  ; done
 
 # 5. Remote blast info gene name + db in species
 ~/software/ncbi-blast-2.6.0+/bin/blastx -db nr -remote -outfmt "6 qseqid sseqid sgi sblastnames stitle pident qlen length mismatch gapope evalue bitscore" -evalue 1e-8 -show_gis -num_alignments 1 -out NCBI_nr_Remote/Blast_nrREMOTE_Chr1InsA_2010EL-1786.xml -query ALLCDS_Chr1InsA_Ins1A_chr1_2010EL-1786.fa -entrez_query  "Vibrio cholerae [Organism]"


