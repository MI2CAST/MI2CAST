#  Example of two transcription factors regulating the expression of a gene (draft)

This example of genetic regulation is based on the following paper: "[Induction of the RelB NF-kappaB subunit by the cytomegalovirus IE1 protein is mediated via Jun kinase and c-Jun/Fra-2 AP-1 complexes.](https://dx.doi.org/10.1128%2FJVI.79.1.95-105.2005)" by Wang and Sonenshein (2005). It describes the causal interaction between a complex of two transcription factors (JUN and FOSL2) that activates the transcription of the RELB gene:

<p align="center">
  <img src="https://github.com/vtoure/MI2CAST/blob/master/images/2tf-tg.svg" alt="2TF-TG regulation"/>
</p>


## Annotation of the causal interaction following MI2CAST

| Term                         | Identifier      | Name/Label                                            | Database                          |
|------------------------------|-----------------|-------------------------------------------------------|-----------------------------------|
| source                       | P05412 *and* P15408 | JUN *and* FOSL2                                   | Uniprot                           |
| target                       | 5971            | RELB                                                  | Entrez gene                       |
| regulation sign              | 2235            | up-regulates                                          | PSI-MI                            |
| reference                    | 15596805        | "Induction of the RelB NF-kappaB subunit..."          | Pubmed                            |
| evidence                     | 0007682         | reporter gene assay evidence used in manual assertion | Evidence and Conclusion Ontology  |
| biological mechanism         | 2247            | transcription regulation                              | PSI-MI                            |
| compartment of interaction   | 0005634         | nucleus                                               | GO:CC                             |
| taxon                        | 9606            | Homo sapiens                                          | NCBI taxonomy                     |
| cell line                    | 0000944         | NIH-3T3 cell                                          | BRENDA                            |
| experimental setup source    | 0506            | over expressed level                                  | PSI-MI                            |
| experimental setup target    | 0000832         | promoter_region                                       | Sequence Ontology                 |


## Written explanation of the causal statement
JUN and FOSL2 are two proteins (transcription factors) that bind together to form a complex. This complex up-regulates the transcription of RELB gene. This causal statement is a manual assessement from a reporter gene assay described in Wang and Sonenshein's article. The experiment has been designed in such a way that both all entities were engineered: the source entities were both overexpressed and the target (RELB) was represented by its promoter regulatory region, which is involved in the transcription process. This causal statement has been observed in human, specifically in this case, in the nucleus of a NIH-3T3 cell.

> Note: The two source entities bind together and form a complex. However, this complex does not have a defined identifier in the ComplexPortal database. Thus to define this entity, we have used the Uniprot ID of both entities, and we link them with an *and* relation meaning that both entities are necessary to observe the causal effect on the target.
