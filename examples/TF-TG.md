#  Example of transcription factor target gene causal statement

This example of genetic regulation is based on the following paper: "[Characterization of E2F8, a novel E2F-like cell-cycle regulated repressor of E2F-activated transcription](https://doi.org/10.1093/nar/gki855)" by Christensen et al. (2005) . It describes the causal interaction between a transcription factor E2F8 that represses the transcription of the CCNE1 gene:

<p align="center">
  <img src="https://github.com/vtoure/MI2CAST/blob/master/images/tf-tg.svg" alt="TF-TG regulation"/>
</p>


## Annotation of the causal interaction following MI2CAST

| Term | Identifier | Name/Label | Database |
|---|---|---|---|
| source | [UniProtKB:A0AVK6](https://www.uniprot.org/uniprot/A0AVK6) | E2F8 | UniProt |
| target | [Entrez:898](https://www.ncbi.nlm.nih.gov/gene/898) | CCNE1 | Entrez gene |
| effect | [MI:2240](http://purl.obolibrary.org/obo/MI_2240) | down-regulates | PSI-MI |
| reference | [PMID:16179649](https://www.ncbi.nlm.nih.gov/pubmed/16179649) | "Characterization of E2F8, a novel..." | Pubmed |
| evidence | [ECO:0005648](http://purl.obolibrary.org/obo/ECO_0005648) | luciferase reporter gene assay evidence used in manual assertion | Evidence and Conclusion Ontology |
| biological mechanism | [MI:2247](http://purl.obolibrary.org/obo/MI_2247) | transcriptional regulation | PSI-MI |
| compartment interaction | [GO:0005634](http://purl.obolibrary.org/obo/GO_0005634) | nucleus | GO:CC |
| taxon source | [NCBI:txid9606](http://purl.obolibrary.org/obo/NCBITaxon_9606) | Homo sapiens | NCBI taxonomy |
| taxon source | [NCBI:txid9606](http://purl.obolibrary.org/obo/NCBITaxon_9606) | Homo sapiens | NCBI taxonomy |
| cell line | [BTO:0001938](http://purl.obolibrary.org/obo/BTO_0001938) | human osteosarcoma cell line | BRENDA |
| experimental setup source 1 | [MI:0506](http://purl.obolibrary.org/obo/MI_0506) | over expressed level | PSI-MI |
| experimental setup source 2 | [MI:0331](http://purl.obolibrary.org/obo/MI_0331) | engineered | PSI-MI |
| experimental setup target 1 | [MI:0331](http://purl.obolibrary.org/obo/MI_0331) | engineered | PSI-MI |
| experimental setup target 2 | [SO:0001679](http://purl.obolibrary.org/obo/SO_0001679) | transcription\_regulatory\_region| Sequence Ontology |


## Written explanation of the causal statement
E2F8 is a protein that down-regulates the transcription of CCNE1 gene. This causal statement has been a manually assessed from a luciferase reporter gene assay that is described in the Christensen et al.'s article. In the experiment, both entities were engineered: CCNE1's transcription regulatory region only and E2F8 has been overexpressed. This causal statement occurs in human, specifically in this example, in the nucleus of the human osteosarcoma cell.

## Formats

The file formats given below try to describe in the best possible way the example shown above, complying with the formats' standards.  

[PSI-MITAB2.8](/MI2CAST/examples/files/TF-TG.tab)  
> Note: The evidence is annotated with a PSI-MI CV term ("MI:0686" - reporter gene assay) as PSI-MITAB only allows the use of MI CV for this column.  


causalJSON.. in preparation.
