# MICAST Guideline (under construction)

The MICAST guideline describes the minimum information  that is necessary to depict causal interactions in Biology. The aim is to homogeneise the representation of causality within the community to make the data generated “FAIR” (Findable, Accessible, Interoperable and Reproducible). 

This guideline targets curators and data providers interested in the representation of causality in molecular interactions and biological systems. 


## Introduction to causality statements

A causality statement is a binary directed interaction between two biological entities where the *source entity* regulates and has an influence on the activity or the quantity of the *target entity*. The *causal interaction* can be direct (without intermediates) or indirect (the causal impact of *source entity* is transmitted to the *target entity* by a third).
Consequently, a causal statement is composed of three type of elements: the *source entity*, the *causal interaction* and the *target entity*. 

In MICAST, we define the object __Entity__ for representing the source and target entities, and the object __Causal Interaction__ for representing the causal interaction. 

Furthermore, the challenge of representing causality statements relies on capturing enough contextual information about the elements that compose the causality statement. The context is important to define boundaries under which a specific causal statement is true. We would like to define this as a __Context__ object.


Each object can contain a certain number of mandatory terms that will be clarified below. For each term, recommendations of ontologies to use to depict the data are suggested. We strongly advise to follow the recommendations.


## Defining __Entity__ objects 
The __Entity__ object can either be a source (the regulator) or a target (the regulated). The nature (source or target) of the entity should be explicit. In MICAST, we consider the following terms mandatory to be defined for representing an __Entity__: Identifier, Name, Type, Activity.

### Identifier
Unique identification number represented as follow: *databaseName:identifier*. For example: `uniprotkb:A12345`

We recommend to use different ontologies depending on the type of the biological entity:
* Gene: [ensembl gene ID](http://www.ensembl.org), [ncbi gene ID](https://www.ncbi.nlm.nih.gov/gene)
* RNA (non coding): [rna central ID](http://rnacentral.org/)
* mRNA: 
  * Recommended: [ensembl transcript ID](http://www.ensembl.org)
  * Otherwise: [ensembl gene ID](http://www.ensembl.org)
* Protein: [uniprot ID](http://www.uniprot.org/)
* Chemical: [chebi ID](https://www.ebi.ac.uk/chebi/)
* Family: list of strings of [uniprot IDs](http://www.uniprot.org/) (separate each string with a vertical bar "__|__", for example: `A12345|B23456|C34567`)
* Complex:
  * For stable complex: [complexportal ID](https://www.ebi.ac.uk/complexportal/home)
  * For transient complex: list of strings of [uniprot](http://www.uniprot.org/) or [chebi](https://www.ebi.ac.uk/chebi/) IDs in alphanumerical order (separate each string with a vertical bar "__|__") 
* Phenotype: [gene ontology ID](http://www.geneontology.org/)
* Stimulus: To be discussed, see issue [#2](https://github.com/vtoure/MICAST/issues/2).

### Name 
String representing the given name/alias of the entity. This could be used for visualisation purposes.

### Type
The biological type of the entity involved (e.g, gene, RNA, mRNA, protein, chemical, phenotype, etc). We recommend to use the [Molecular Interaction Controlled Vocabulary](https://www.ebi.ac.uk/ols/ontologies/mi), specifically the branches [causal interactor type](https://www.ebi.ac.uk/ols/ontologies/mi/terms?iri=http%3A%2F%2Fpurl.obolibrary.org%2Fobo%2FMI_2259) and [interactor type](https://www.ebi.ac.uk/ols/ontologies/mi/terms?iri=http%3A%2F%2Fpurl.obolibrary.org%2Fobo%2FMI_0313)

### Activity
The molecular function that is involved in the causal interaction. To be discussed, see issue [#3](https://github.com/vtoure/MICAST/issues/3).



## Defining __Causal Interaction__ objects
The __Causal Interaction__ object is the core element of a causality statement. In MICAST, we consider the following terms mandatory to be defined for representing a __Causal Interaction__: Regulation, Mechanism, Localisation, Evidence, Reference.

### Regulation 
The type of regulation exerced by the source entity upon the target entity. Recommendation to come.

### Mechanism
The modification that happens to the target __Entity__ (e.g, phosphorylation, binding, etc).  We recommend to use the [Molecular Interaction Controlled Vocabulary](https://www.ebi.ac.uk/ols/ontologies/mi), branch [causal interaction](https://www.ebi.ac.uk/ols/ontologies/mi/terms?iri=http%3A%2F%2Fpurl.obolibrary.org%2Fobo%2FMI_2233) or branch [interaction type](https://www.ebi.ac.uk/ols/ontologies/mi/terms?iri=http%3A%2F%2Fpurl.obolibrary.org%2Fobo%2FMI_0190).

### Localisation 
Description of the localisation of the causal interaction. The causal interaction can occur inside a cell or between two cells. We recommend to use the [Gene Ontology Cellular Component](http://geneontology.org/) (GO:CC). Alternatively it could also be represented with a combination of GO:CC and the host organism (Species)/Cell Type (to be further developed).

### Evidence
The Evidence is a proof of the existence of the causal interaction (e.g, experimental technique, literature curation, computational method, etc). We recommend to use the [Evidence & Conclusion Ontology](http://www.evidenceontology.org/)

### Reference
Publication identifier in which the causality statement has been highlighted. We recommend to provide the pubmed ID. It could also be a list of references, in that case, separate the different pubmed IDs with a vertical bar "|".

### Text
Free text field that should contain the exact sentence from the reference where the causal interaction is mentionned. 



## Defining __Context__ objects

### Species
Type of species where the causal interaction is observed. We recommend to use the [Taxonomy ID](https://www.ncbi.nlm.nih.gov/taxonomy) from NCBI. For example: `9606` for *Homo sapiens*.

### Cell Type
Cell type where the causal interaction occurs. Currently, we can recommend to use [BRENDA](https://www.brenda-enzymes.org/ontology.php?ontology_id=3), [Cellosaurus](https://web.expasy.org/cellosaurus/) or [Cell Ontology](https://obofoundry.org/ontology/cl.html). But the recommendations need to be discussed, see issue [#5](https://github.com/vtoure/MICAST/issues/5).

### Tissue Type
Tissue type where the causal interaction occurs. We recommend to use either [BRENDA](https://www.brenda-enzymes.org/ontology.php?ontology_id=3) or [Uberon](http://uberon.github.io/about.html).



## Summary
In this section, we provide tables summarising the list of terms necessary for the three objects defined above, along with an example for each term.

### Summary of terms used for Entity

| Term | Ontology | Example  (meaning)|
|---|---|---|
| Identifier | type dependent | `uniprotkb:P31749` |
| Name | free text | `AKT1` |
| Type | MI | `MI:0326` (protein)|

### Summary of terms used for Causal Interaction
| Term | Ontology | Example (Meaning) |
|---|---|---|
| Regulation | ? | ? |
| Mechanism | MI | `MI:0220` (ubiquitination reaction) |
| Localisation | GO:CC | `GO:0005829` (cytosol) |
| Evidence | ECO | `ECO:0001089` (in vivo ubiquitination assay evidence) |
| Reference | Pubmed | `22410793` |
| Text | free text | `the degradation of Akt by MULAN suppresses cell proliferation and viability.` |

### Summary of terms used for Context
| Term | Ontology | Example (meaning) |
|----|----|----|
| Species | NCBI Taxonomy | `9606` (*Homo sapiens*) |
| Cell Type | BRENDA / Cellosaurus / CL | `BTO:0002733` (embryonic kidney cell line) |
| Tissue Type | BRENDA / Uberon | `UBERON:0004819` (kidney epithelium) |


## Format
In this section, we will provide a list of formats that follows the MICAST guidelines to represent causality statements.
 
## Examples
Concrete example of causality statements. 

## Contributors
Vasundra Touré ([vasundra.toure@ntnu.no](mailto:vasundra.toure@ntnu.no))

*Please add your name here*
