# Formalising the representation of Causal Statements
<div style="text-align: justify">
The MICAST (Minimum Information about a Causal Statement) guideline describes information that are necessary to depict causal interactions in molecular biology. The aim is to homogeneise their representation for a better usability and understanding, by making the data “FAIR” (Findable, Accessible, Interoperable and Reproducible). 

This guideline targets curators and data providers of causality in molecular interactions and biological systems, but also tool developers, text miners to know what type of information can be expected when dealing with causal statements.
</div>

## Introduction to causal statements

<div style="text-align: justify">
A causal statement is a directed interaction between biological entities where a *source entity* (regulator) regulates and has an influence on the activity or the quantity of a *target entity* (regulated entity). The *causal interaction* can be direct (without intermediates) or indirect (the causal impact of *source entity* is transmitted to the *target entity* by a third).

The core of a causal statement is composed of three type of elements: the *source entity*, the *causal interaction* (representing the regulation) and the *target entity*. 

<p align="center">
  <img src="https://github.com/vtoure/MICAST/blob/master/images/causalStatement.svg" alt="Causal statement"/>
</p>

Furthermore, one big challenge relies on capturing enough contextual information to gradually enrich a causal statement and define boundaries under which it is true. This type of information may be diffuse and difficult to curate. With this guideline, we hope to formalise the depiction of that metadata in order to obtain contextualised causal statements that can be used for many applications in systems biology and systems medicine.
</div>

## The information content of MICAST
The contextual information in MICAST is split and categorized into different levels of requirement.

Four levels are defined:
- CAUSALITY reflects the core of a causal statement showing the causality, the mandatory layer of information
- CONDITION reflects the constraints under which the causal statement is applied or has been observed
- QUALITY provides details about the assessment of the causal statement
- SUPPORTING DATA indicate additional information that provides mechanistic details.

Each level defines specific terms that will be detailed in the sections below. For each term, recommendations on ontologies and controlled vocabularies to use are suggested. We strongly advise to follow the recommendations.

## Notation conventions

We follow the conventions of the [RFC keywords](https://tools.ietf.org/html/rfc2119) to indicate the requirement levels:
* __MUST__ : absolute requirement for a causal statement
* __SHOULD__ : required for a causal statement when adequate (case specific)


## CAUSALITY
In the CAUSALITY level, a __Causal Statement__ contains a Source Entity, a Target Entity and a Regulation. Every term in this level is mandatory.
We define the object __Entity__  which can either be a source (the regulator) or a target (the regulated).

### Entity (MUST)
A unique identifier helps to identify the specific biological entity involved in the causal statement.
Source Entity and Target Entity are child terms of __Causal Statement__.

We recommend to use different ontologies depending on the type of the biological entity:
* Gene: [ensembl gene ID](http://www.ensembl.org), [Entrez gene ID](https://www.ncbi.nlm.nih.gov/gene)
* RNA (non coding): [rna central ID](http://rnacentral.org/)
* mRNA: 
  * Recommended: [ensembl transcript ID](http://www.ensembl.org)
  * Otherwise: [ensembl gene ID](http://www.ensembl.org)
* Protein: [uniprot ID](http://www.uniprot.org/)
* Chemical: [chebi ID](https://www.ebi.ac.uk/chebi/)
* Family: list of strings of IDs following the rules (for a family gene, use ensembl gene ID or Entrez gene ID, for a protein family, use uniprot IDs, etc). Separate each string with a vertical bar "__|__", for example: `A12345|B23456|C34567`
* Complex:
  * For stable complex: [complexportal ID](https://www.ebi.ac.uk/complexportal/home)
  * For transient complex: list of strings of [uniprot](http://www.uniprot.org/) or [chebi](https://www.ebi.ac.uk/chebi/) IDs in alphanumerical order. Separate each string with a vertical bar "__|__" 
* Phenotype: [gene ontology ID](http://www.geneontology.org/)
* Stimulus: To be discussed, see issue [#2](https://github.com/vtoure/MICAST/issues/2).

### Regulation (MUST)
The type of regulation exerced by the source __Entity__ upon the target __Entity__ in the __Causal Statement__. Regulation is a child term of __Causal Statement__.

Ontology recommendation: 
* [Molecular Interaction](https://www.ebi.ac.uk/ols/ontologies/mi/terms?iri=http%3A%2F%2Fpurl.obolibrary.org%2Fobo%2FMI_2234)
*  [Relation Ontology](https://www.ebi.ac.uk/ols/ontologies/ro/properties?iri=http%3A%2F%2Fpurl.obolibrary.org%2Fobo%2FRO_0002506).

### Type (SHOULD)
The biological type of the __Entity__ involved (e.g, gene, RNA, mRNA, protein, chemical, phenotype, etc). Type is a child term of __Entity__.

Ontology recommendation: [Molecular Interaction Controlled Vocabulary](https://www.ebi.ac.uk/ols/ontologies/mi) - branch  [interactor type](https://www.ebi.ac.uk/ols/ontologies/mi/terms?iri=http%3A%2F%2Fpurl.obolibrary.org%2Fobo%2FMI_0313)


## CONDITION
The CONDITION level informs about necessary circumstances under which a __Causal Statement__ has been observed or proven to be true: Is the entity phosphorylated? Does the causality occurs in a specific tissue? etc.

### State (SHOULD)
Information about the state of the source or the target __Entity__ necessary for the causal regulation to occur (e.g, the source should be phosphorylated at residue XXX in position YYY to up-regulate the target). Recommendation to come. State is a child term of __Entity__.

## Experimental preparation (SHOULD)
A source or target __Entity__ can be represented by a specific experimental setup which could explain the causal character of the __Causal Statement__. For example, an overexpression of a gene.

Ontology recommendation: [Molecular Interaction Controlled Vocabulary](https://www.ebi.ac.uk/ols/ontologies/mi) - branch [experimental preparation](https://www.ebi.ac.uk/ols/ontologies/mi/terms?iri=http%3A%2F%2Fpurl.obolibrary.org%2Fobo%2FMI_0346). Experimental preparation is a child term of __Entity__.

## Experiment type (SHOULD)
The __Causal Statement__ can be assessed from a particular experiment type. Experiment type is a child term of __Causal Statement__.

Ontology recommendation: [Evidence & Conclusion Ontology](http://www.evidenceontology.org/).

### Species (SHOULD)
Type of species where the __Causal Statement__ is observed. 
Species can also refer to the type of species of the source or target __Entity__ to distinguish causality assessed with entities from different species. In some cases, the species information is implicitly defined in the Entity's identifier. Species is a child term of __Causal Statement__ and __Entity__.

Ontology recommendation: [Taxonomy ID](https://www.ncbi.nlm.nih.gov/taxonomy) from NCBI.

### Cell Line, Tissue or Cell Type (SHOULD)
Cell line where the __Causal Statement__ is observed or, tissue or cell type where the causal interaction occurs. Cell Line, Tissue or Cell Type is a child term of __Causal Statement__.

Ontology recommendation:
* [BRENDA](https://www.brenda-enzymes.org/ontology.php?ontology_id=3)
* [Cell Ontology](http://www.obofoundry.org/ontology/cl.html) 
* [Uberon](http://uberon.github.io/) 
See discussions  [#5](https://github.com/vtoure/MICAST/issues/5).

### Compartment (SHOULD)
Description of the cellular localisation of the __Causal Statement__. The causal interaction can occur inside a cell or between two cells. Compartment is a child term of __Causal Statement__.

Ontology recommendation:  [Gene Ontology Cellular Component](http://geneontology.org/) (GO:CC).


## QUALITY
The quality level provides information about the assessment and the provenance of the __Causal Statement__: In which publication this causal relationship has been found? What the causal interaction manually curated or automatically generated?
This provides some criteria to rank the trust in the annotated causal statement.

### Evidence (MUST)
The Evidence states how the existence of the __Causal Statement__ has been proved (e.g, experimental technique, literature curation, computational method, etc). This information helps the user of the data to know how to trust this causal statement. Evidence is a child term of __Causal Statement__.

Ontology recommendation:  [Evidence & Conclusion Ontology](http://www.evidenceontology.org/)

### Reference (SHOULD)
Publication identifier in which the causal statement has been highlighted. This is a quality assessment term. We recommend to provide the pubmed ID. It could also be a list of references, in that case, separate the different pubmed IDs with a vertical bar "|". Reference is a child term of __Causal Statement__.

Ontology recommendation: [PubMed ID](https://www.ncbi.nlm.nih.gov/pmc/pmctopmid/)


## SUPPORTING DATA
The supporting data represent mechanistic details about the __Causal Statement__. Two terms are suggested: Activity and Mechanism. 


### Activity (SHOULD)
The molecular function of the __Entity__ that is involved in the __Causal Statement__: meaning the function of the __Entity__ that causes the regulation or that is regulated. Activity is a child term of Entity. 

Ontology recommendation: [Gene Ontology Molecular Function](http://geneontology.org/) (GO:MF). 
To be further discussed, see issue [#3](https://github.com/vtoure/MICAST/issues/3).

### Mechanism (SHOULD)
The modification involved in the __Causal Statement__, that targets the target __Entity__ (e.g, phosphorylation, binding, etc). Mechanism is a child term of __Causal Statement__

Ontology recommendation:
* [Molecular Interaction Controlled Vocabulary](https://www.ebi.ac.uk/ols/ontologies/mi) - branch [causal interaction](https://www.ebi.ac.uk/ols/ontologies/mi/terms?iri=http%3A%2F%2Fpurl.obolibrary.org%2Fobo%2FMI_2233)
* [Molecular Interaction Controlled Vocabulary](https://www.ebi.ac.uk/ols/ontologies/mi) - branch [interaction type](https://www.ebi.ac.uk/ols/ontologies/mi/terms?iri=http%3A%2F%2Fpurl.obolibrary.org%2Fobo%2FMI_0190).


## Summary
The following graph provides an overview of the list of terms by highlighting the layer they belong to in MICAST.



## MICAST Supports
In this section, we will provide a list of formats or tools that support the MICAST guidelines to represent causal statements.


## Contributors
Vasundra Touré ([vasundra.toure@ntnu.no](mailto:vasundra.toure@ntnu.no))

