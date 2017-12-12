# MICAST Guideline (under construction)

The MICAST guideline describes the minimum information  that is necessary to depict causal interactions in Biology. The aim is to homogeneise the representation of causality within the community to make the data “FAIR” (Findable, Accessible, Interoperable and Reproducible). 

This guideline targets curators and data providers interested in the representation of causality in molecular interactions and biological systems. 


## Introduction to causality statements

A causality statement is a binary directed interaction between two biological entities where the *source entity* regulates and has an influence on the activity or the quantity of the *target entity*. The *causal interaction* can be direct (without intermediates) or indirect (the causal impact of *source entity* is transmitted to the *target entity* by a third).
Consequently, a causal statement is composed of three type of elements: the *source entity*, the *causal interaction* and the *target entity*. 

In MICAST, we define the object __Entity__ for representing the source and target entities, and the object __Causal Interaction__ for representing the causal interaction. 

Furthermore, the challenge of representing causality statements relies on capturing enough contextual information about the elements that compose the causality statement. The context is important to define boundaries under which a specific causal statement is true. We would like to define this as a __Context__ object.


Each object can contain a certain number of mandatory terms that will be clarified below. For each term, recommendations of ontologies to use to depict the data are suggested. Whenever it is possible, we strongly advise to follow the recommendations.


## Defining __Entity__ objects 
The __Entity__ object can either be a source (the regulator) or a target (the regulated). In MICAST, we consider the following terms mandatory to be defined for representing an __Entity__: Identifier, Name, Type, Activity.

### Identifier
Unique identification number represented as follow: *databaseName:identifier*. For example: uniprotkb:A12345

We recommend to use different ontologies depending on the type of the biological entity:
* Gene: [ensembl gene ID](http://www.ensembl.org), [ncbi gene ID](https://www.ncbi.nlm.nih.gov/gene)
* RNA (non coding): [rna central ID](http://rnacentral.org/)
* mRNA: 
  * Recommended: [ensembl transcript ID](http://www.ensembl.org)
  * Otherwise: [ensembl gene ID](http://www.ensembl.org)
* Protein: [uniprot ID](http://www.uniprot.org/)
* Chemical: [chebi ID](https://www.ebi.ac.uk/chebi/)
* Family: list of strings of [uniprot IDs](http://www.uniprot.org/) (separate each string with a vertical bar "__|__", for example: A12345|B23456|C34567)
* Complex:
  * For stable complex: [complexportal ID](https://www.ebi.ac.uk/complexportal/home)
  * For transient complex: list of strings of [uniprot](http://www.uniprot.org/) or [chebi](https://www.ebi.ac.uk/chebi/) IDs in alphanumerical order (separate each string with a vertical bar "__|__") 
* Phenotype: [gene ontology ID](http://www.geneontology.org/)
* Stimulus: To be discussed, see issues.

### Name 
String representing the given name/alias of the entity. This could be used for visualisation purposes.

### Type
The biological type of the entity involved (e.g, gene, RNA, mRNA, protein, chemical, phenotype, etc). We recommend to use the [Molecular Interaction Controlled Vocabulary](https://www.ebi.ac.uk/ols/ontologies/mi), specifically the branches [causal interactor type](https://www.ebi.ac.uk/ols/ontologies/mi/terms?iri=http%3A%2F%2Fpurl.obolibrary.org%2Fobo%2FMI_2259) and [interactor type](https://www.ebi.ac.uk/ols/ontologies/mi/terms?iri=http%3A%2F%2Fpurl.obolibrary.org%2Fobo%2FMI_0313)

### Activity
The molecular function that is involved in the causal interaction. To be discussed, see issues.




## Defining __Causal Interaction__ objects
The __Causal Interaction__ object is the core element of a causality statement. In MICAST, we consider the following terms mandatory to be defined for representing a __Causal Interaction__: Regulation, Mechanism, Localisation, Evidence, Reference.

### Regulation 
The type of regulation exerced by the source entity upon the target entity. Recommendation to come.

### Mechanism
The modification that happens to the target __Entity__ (e.g, phosphorylation, binding, etc).  We recommend to use the [Molecular Interaction Controlled Vocabulary](https://www.ebi.ac.uk/ols/ontologies/mi), branch [causal interaction](https://www.ebi.ac.uk/ols/ontologies/mi/terms?iri=http%3A%2F%2Fpurl.obolibrary.org%2Fobo%2FMI_2233).

### Localisation 
Description of the localisation of the causal interaction. The causal interaction can occur inside a cell or between two cells. We recommend to use the [Gene Ontology Cellular Component](http://geneontology.org/) (GO:CC). Alternatively it could also be represented with a combination of GO:CC and the host organism (Species)/Cell Type (to be further developed).

### Evidence
The Evidence is a proof of the existence of the causal interaction (e.g, experimental technique, literature curation, computational method, etc). We recommend to use the [Evidence & Conclusion Ontology](http://www.evidenceontology.org/)

### Reference
Publication identifier in which the causality statement has been highlighted. We recommend to provide the pubmed ID. Example: pubmed:1234567
It could also be a list of references, in that case, separate the different pubmed IDs with a vertical bar "|".

### Text
Free text field that should contain the exact sentence from the reference where the causal interaction is mentionned. 

## Defining __Context__ objects
### Causal observations
#### Species
#### Cell Type
#### Tissue Type

## Summary
In this section, we will provide a table summarising the terms of each object defined above.

## Format
In this section, we will provide a list of formats that follow the MICAST guidelines to represent causality statements.
 
## Examples
Concrete example of causality statements. 

## Contributors
Vasundra Touré (vasundra.toure@ntnu.no)

*more to be added*
