KEGG Mappings
=============

This package is intended as a fast mapping tool for gene - ortholog pairs

Dependencies:
gnu-parallel, wget and curl

Installation:
-------------

1. Clone this repo
2. Create a kegg directory in your ``$HOME`` folder (i.e. ``mkdir -p $HOME/kegg``)
3. Move all the compressed files to your kegg folder
4. Put the .sh scripts in your ``$PATH`` and give them execution permissions (i.e. ``chmod 775 get_pathways.sh``)
5. Adjust the variables ``kegg_data_dir``, ``kegg_tmp_dir`` and the number of threads employed by parallel

Usage
-----

We provide a simple exaple of a list of genes and a control file

```bash
head example.tsv
gene_1	KO:K10411
gene_2	KO:K10847
gene_3	KO:K02291
gene_4	KO:K00621
gene_5	KO:K08906
gene_6	KO:K05655
gene_7	KO:K12896
gene_8	KO:K03135
gene_9	KO:K08293
gene_10	KO:K05906

cat example.dat
org include	cre,ath,ota
org exclude	hsa,mmu
annotation file	example.tsv
```

``get_pathways_parallel.sh`` reads the control file in which the user can specify a list of organisms to include in the mappings and a list of organisms to exclude from the mappings (a comprehensive list of KEGG organisms can be found [here](https://www.genome.jp/kegg/catalog/org_list.html))

In the example control file (``example.dat``), ``get_pathways_parallel.sh`` will process ``example.tsv`` mapping pathways from *Chlamydomonas reinhardtii*, *Arabidopsis thaliana* and *Ostreococcus tauri* (cre,ath,ota) but excluding pathways from man and mouse.

```bash
get_pathways_parallel.sh example.dat > example_results.tsv
ortholog_gene_mappings file present
org_list file present
pathway_list file present
gene_pathway_mappings file present
```
