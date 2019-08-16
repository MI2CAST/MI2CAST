#  Example of transcription factor target gene causal statement

This example is based on the following paper: "Characterization of E2F8, a novel E2F-like cell-cycle regulated repressor of E2F-activated transcription" [(DOI)](https://doi.org/10.1093/nar/gki855). It describes the causal interaction between a transcription factor E2F8 that represses the transcription of the CCNE1 gene:

<p align="center">
  <img src="https://github.com/vtoure/MI2CAST/blob/master/images/tf-tg.svg" alt="causal statement"/>
</p>


## Annotation of the causal interaction following MI2CAST

| Term                         | Identifier | Name/Label                                     | Database                          |
|------------------------------|------------|------------------------------------------------|-----------------------------------|
| source                       | A0AVK6     | E2F8                                           | Uniprot                           |
| target                       | 898        | CCNE1                                          | Entrez gene                       |
| regulation sign              | 2240       | down-regulates                                 | PSI-MI                            |
| reference                    | 16179649   | -                                              | Pubmed                            |
| evidence 1                   | 0000269    | experimental evidence used in manual assertion | Evidence and Conclusion Ontology  |
| evidence 2                   | 0001805    | luciferase reporter gene assay evidence        | Evidence and Conclusion Ontology  |
| biological mechanism         | 2247       | transcription regulation                       | PSI-MI                            |
| compartment of interaction   | 0005634    | nucleus                                        | GO:CC                             |
| taxon                        | 9606       | Homo sapiens                                   | NCBI taxonomy                     |
| cell line                    | 0001938    | human osteosarcoma cell line                   | BRENDA                            |
| experimental setup source 1  | 0506       | over expressed level                           | Evidence and Conclusion Ontology  |
| experimental setup source 2  | 0331       | engineered                                     | Evidence and Conclusion Ontology  |
| experimental setup target  1 | 0331       | engineered                                     |  Evidence and Conclusion Ontology |
| experimental setup target 2  | 0001679    | transcription\_regulatory\_region                | Sequence Ontology                 |
