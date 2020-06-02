#  Example of two transcription factors regulating the expression of a gene (draft)

This example of genetic regulation is based on the following paper: "[Induction of the RelB NF-kappaB subunit by the cytomegalovirus IE1 protein is mediated via Jun kinase and c-Jun/Fra-2 AP-1 complexes.](https://dx.doi.org/10.1128%2FJVI.79.1.95-105.2005)" by Wang and Sonenshein (2005). It describes the causal interaction between a complex of two transcription factors (JUN and FOSL2) that activates the transcription of the RELB gene:

<p align="center">
  <img src="https://github.com/vtoure/MI2CAST/blob/master/images/2tf-tg.svg" alt="2TF-TG regulation"/>
</p>


## Annotation of the causal interaction following MI2CAST

| Term | Identifier | Name/Label | Database |
|---|---|---|---|
| source | [UniProtKB:P05412](https://www.uniprot.org/uniprot/P05412) *and* [UniProtKB:P15408](https://www.uniprot.org/uniprot/P15408) | JUN *and* FOSL2 | UniProtKB |
| target | [Entrez:5971](https://www.ncbi.nlm.nih.gov/gene/5971) | RELB | Entrez gene |
| causal relationship | [MI:2235](http://purl.obolibrary.org/obo/MI_2235) | up-regulates | PSI-MI |
| reference | [PMID:15596805](https://www.ncbi.nlm.nih.gov/pubmed/15596805) | "Induction of the RelB NF-kappaB subunit..." | Pubmed |
| evidence | [ECO:0007682](http://purl.obolibrary.org/obo/ECO_0007682) | reporter gene assay evidence used in manual assertion | Evidence and Conclusion Ontology  |
| biological mechanism | [MI:2247](http://purl.obolibrary.org/obo/MI_2247) | transcription regulation | PSI-MI |
| compartment interaction | [GO:0005634]( http://purl.obolibrary.org/obo/GO_0005634) | nucleus | GO:CC |
| taxon source | [NCBI:txid9606](http://purl.obolibrary.org/obo/NCBITaxon_9606) | Homo sapiens | NCBI taxonomy |
| taxon target | [NCBI:txid9606](http://purl.obolibrary.org/obo/NCBITaxon_9606) | Homo sapiens | NCBI taxonomy |
| cell line | [BTO:0000944](http://purl.obolibrary.org/obo/BTO_0000944) | NIH-3T3 cell | BRENDA |
| experimental setup source | [ECO:0005802](http://purl.obolibrary.org/obo/ECO_0005802) | cell transfection evidence used in manual assertion | PSI-MI |
| experimental setup target | [SO:0000832](http://purl.obolibrary.org/obo/SO_0000832) | promoter_region | Sequence Ontology |


## Written explanation of the causal statement

JUN and FOSL2 are two proteins (transcription factors) that bind together to form a complex. This complex up-regulates the transcription of RELB gene. This causal statement is a manual assessement from a reporter gene assay described in Wang and Sonenshein's article. The experiment has been designed in such a way that both entities were engineered: the source entities were both overexpressed and the target (RELB) was represented by its promoter regulatory region, which is involved in the transcription process. This causal statement has been observed in human, specifically in this case, in the nucleus of a NIH-3T3 cell.

> Note: The two source entities bind together and form a complex. However, this complex does not have a defined identifier in the ComplexPortal database. Thus to define this entity, we have used the Uniprot ID of both entities, and we link them with an *and* relation meaning that both entities are necessary to observe the causal effect on the target.

## Written in the Biological Expression Language

This interaction can be encoded in BEL script with the following
metadata and BEL statement. Note that the causal relationship (MI:2235, upregulation) and
biological mechanism (MI:2247, transcription regulation) are reflected in the relationship
type (`->`, increases) and the target entity type (`r`, rnaAbundance), respectively.

```bel
# metadata
SET Citation              = {"PubMed", "15596805"}
SET Taxonomy              = "taxonomy:9606"
SET CellLine              = "bto:0000944"
SET Compartment           = "go:0005634"
SET EvidenceType          = "eco:0007682"
SET ExperimentSetupSource = "eco:0005802 ! cell transfection experiment evidence used in manual assertion"
SET ExperimentSetupTarget = "so:0000832 ! promoter_region"

# BEL Statement
complex(p(uniprot:P05412 ! JUN_HUMAN), p(uniprot:P15408 ! FOSL2_HUMAN)) -> r(ncbigene:5971 ! RELB)
```
