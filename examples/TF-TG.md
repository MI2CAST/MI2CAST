#  Example of transcription factor target gene causal statement

This example is based on the following paper: "[Characterization of E2F8, a novel E2F-like cell-cycle regulated repressor of E2F-activated transcription](https://doi.org/10.1093/nar/gki855)" by Christensen et al. (2005) . It describes the causal interaction between a transcription factor E2F8 that represses the transcription of the CCNE1 gene:

<p align="center">
  <img src="https://github.com/vtoure/MI2CAST/blob/master/images/tf-tg.svg" alt="causal statement"/>
</p>


## Annotation of the causal interaction following MI2CAST

| Term                         | Identifier | Name/Label                                     | Database                          |
|------------------------------|------------|------------------------------------------------|-----------------------------------|
| source                       | A0AVK6     | E2F8                                           | Uniprot                           |
| target                       | 898        | CCNE1                                          | Entrez gene                       |
| regulation sign              | 2240       | down-regulates                                 | PSI-MI                            |
| reference                    | 16179649   | "Characterization of E2F8, a novel..."         | Pubmed                            |
| evidence 1                   | 0000269    | experimental evidence used in manual assertion | Evidence and Conclusion Ontology  |
| evidence 2                   | 0001805    | luciferase reporter gene assay evidence        | Evidence and Conclusion Ontology  |
| biological mechanism         | 2247       | transcription regulation                       | PSI-MI                            |
| compartment of interaction   | 0005634    | nucleus                                        | GO:CC                             |
| taxon                        | 9606       | Homo sapiens                                   | NCBI taxonomy                     |
| cell line                    | 0001938    | human osteosarcoma cell line                   | BRENDA                            |
| experimental setup source 1  | 0506       | over expressed level                           | PSI-MI                            |
| experimental setup source 2  | 0331       | engineered                                     | PSI-MI                            |
| experimental setup target 1  | 0331       | engineered                                     | PSI-MI                            |
| experimental setup target 2  | 0001679    | transcription\_regulatory\_region              | Sequence Ontology                 |


## Written explanation of the causal statement
E2F8 is a protein that down-regulates the transcription of CCNE1 gene. This causal statement is a manual curation from an experimental evidence. The causality of the interaction has been observed with a luciferase reporter gene assay that is described in the Christensen et al.'s article. For the experiment, both entities were engineered: CCNE1's transcription regulatory region only and E2F8 has been overexpressed. This causal statement occurs in human, specifically in this case, in the nucleus of the human osteosarcoma cell.
