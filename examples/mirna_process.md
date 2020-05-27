#  Example of a miRNA regulation a biological process.

This example of miRNA regulation shows the effects of miR-124 on fibroblast proliferation.

When the expression of MicroRNA-124 is experimentally increased, fibroblasts do not proliferate anymore.

<p align="center">
  <img src="https://github.com/vtoure/MI2CAST/blob/master/images/mirna_process.svg" alt="miRNA regulation"/>
</p>


## Annotation of the causal interaction following MI2CAST

| Term | Identifier | Name/Label | Database |
|---|---|---|---|
| source | [RNAcentral:URS000056E1DA_9913](https://rnacentral.org/rna/URS000056E1DA/9913) | Bos taurus (cattle) bta-miR-124 | RNAcentral |
| target | [GO:0048144](http://purl.obolibrary.org/obo/GO_0048144) | fibroblast proliferation | GO:BP |
| causal relationship | [RO:0002430](http://purl.obolibrary.org/obo/RO_0002430) | involved in negative regulation of | RO |
| reference | [PMID:24122720](https://www.ncbi.nlm.nih.gov/pubmed/24122720) | "MicroRNA-124 controls the proliferative... " | Pubmed |
| evidence 1 | [ECO:0005802](http://purl.obolibrary.org/obo/ECO_0005802) | cell transfection experiment evidence used in manual assertion | Evidence and Conclusion Ontology |
| evidence 2 | [ECO:0001235](http://purl.obolibrary.org/obo/ECO_0001235) | MTT assay evidence used in manual assertion | Evidence and Conclusion Ontology |
| cell type | [CL:0002557]( http://purl.obolibrary.org/obo/GO_0005737) | fibroblast of pulmonary artery | CL |
| experimental setup source 1 | [MI:0506](http://purl.obolibrary.org/obo/MI_0506) | over expressed level | PSI-MI |
| experimental setup source 2 | [MI:0331](http://purl.obolibrary.org/obo/MI_0331) | engineered | PSI-MI |


## Written explanation of the causal statement
The Bos baurus miRNA-124 is involved in the negative regulation of the fibroblast proliferation process. This regulation is observed in a fibroblast of pulmonary artery cell, through a combination of a cell transfection experiment and an MTT assay described in the following publication: ["MicroRNA-124 controls the proliferative, migratory, and inflammatory phenotype of pulmonary vascular fibroblasts." by Wang et al.](https://doi.org/10.1161/CIRCRESAHA.114.301633). In these experiments, engineered miRNA-124 has been over-expressed in fibroblasts.

## Formats

The file formats given below try to describe in the best possible way the example shown above, complying with the formats' standards.  

[causalJSON](https://github.com/MI2CAST/MI2CAST/blob/master/examples/files/mirna_process.json)  

## Written in the Biological Expression Language

```bel
# metadata
SET Citation              = {"PubMed", "24122720"}
SET CellLine              = "cl:0002557"
SET EvidenceType          = {"eco:0005802", "eco:0001235"}
SET ExperimentSetupSource = {"mi:0506", "mi:0331"}

# BEL Statement
m(rnacentral:URS000056E1DA_9913 ! "Bos taurus (cattle) bta-miR-124") -| bp(go:0048144 ! "fibroblast proliferation")
```
