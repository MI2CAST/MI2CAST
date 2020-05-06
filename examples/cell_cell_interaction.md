# Cell to cell causal interaction

This example illustrates one of the possible future developments of MI2CAST, namely cells as valid source and target entities. The selected paper is the following: “Interleukin-21 promotes germinal center reaction by skewing the follicular regulatory T cell to follicular helper T cell balance in autoimmune BXD2 mice” [PMID:24909430](https://doi.org/10.1002/art.38735), that reports a causal interaction between the follicular Treg cell and GC B cell. By following the rules of MI2CAST, it is possible to annotate the following information:

## Possible annotation of the causal interaction

### Rule 1: Source and Target entities
CL:0000815 (Regulatory T cell): the source entity is the regulatory T cell annotated with a Cell Ontology term identifier.
CL:0000844 (Germinal center B cell): the target entity is the germinal center B cell annotated with a Cell Ontology term identifier.

### Rule 2: Effect
MI:2240 (down-regulates): the effect of the causal interaction is a down-regulation, annotated with an MI controlled vocabulary term. Regulatory T cell down-regulates Germinal center B cell. 

### Rule 3:
#### 3.1: Reference
PMID:24909430: the causal statement is assessed in the article entitled “Interleukin-21 promotes germinal center reaction by skewing the follicular regulatory T cell to follicular helper T cell balance in autoimmune BXD2 mice”. The PubMed identifier is given.

#### 3.2: Evidence type
ECO:0005581 (enzyme-linked immunoabsorbent assay evidence used in manual assertion): the observation of the causal interaction is done via an ELISA and has been extracted through a human review. An Evidence and Conclusion Ontology identifier is given. 

### Rule 4:
#### 4.1: Biological activity or mechanism:
GO:0045578 (negative regulation of B cell differentiation): the biological mechanism of the causal interaction is a negative regulation of B cell differentiation, annotated with a Gene Ontology term. Regulatory T cell is a regulator of germinal center B cells.

##### 4.2: The biological type
The biological type of the source and target entities is not necessary to be annotated as the correct identifiers have been given: both entities are cells annotated with a Cell Ontology term identifier.

#### 4.3: Biological modification
There is no information about a specific biological modification of the source nor the target entity in this article, thus no annotation is added for Rule 4.3.

#### 4.4: Taxon
NCBI:txid10116 (Mus musculus): both the source and target entity belongs to mouse, and the causal interaction is assessed in cells extracted from mouse tissues, thus the taxonomy is annotated as being from mouse. 

#### 4.5.3: Cell line
When we describe causal interactions between cells, it is not necessary to inform cell line.

#### 4.5.4: Cellular component 
When we describe causal interactions between cells, it is not necessary to inform the cellular component.

#### 4.6: Experimental setup
ECO:0005580 (flow cytometry evidence used in manual assertion) for the source entity: The source entity has been identified and collected through flow cytocmetry during the experiment, annotated with an ECO term.
MI:0421 (Identification by antibody) for the target entity: the target entity has been identified via antibody binding during the experiment, annotated with a MI term.

## Written in the Biological Expression Language

```bel
# metadata
SET Citation              = {"PubMed", "24122720"}
SET Taxonomy              = "taxonomy:10116 ! Mus musculus"
SET EvidenceType          = "eco:0005581 ! enzyme-linked immunoabsorbent assay evidence used in manual assertion"
SET ExperimentSetupSource = "eco:0005580 ! flow cytometry evidence used in manual assertion"
SET ExperimentSetupTarget = "mi:0421 ! Identification by antibody"

# BEL Statement
pop(cl:0000815 ! "Regulatory T cell") =| act(pop(cl:0000844 ! "Germinal center B cell"), ma(go:0030183 ! "B cell differentiation")
```

Since BEL encodes the polarity of a mechanism in the relationship, the activity of the germinal center B cell
is set to be GO:0030183 (B cell differentiation), which is the parent apolar term of 
GO:0045578 (negative regulation of B cell differentiation).

Note, using the `act()` function in combination with the `pop()` function might not technically be BEL
standards-compliant, but with appropriate examples such as this, it can be added through a BEL enhancement
proposal.
