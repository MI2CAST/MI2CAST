# Formalising the representation of Causal Statements (under construction)

The following guideline describes information that are necessary to depict causal interactions in molecular biology. The aim is to homogeneise their representation for a better usability and understanding, by making the data “FAIR” (Findable, Accessible, Interoperable and Reproducible). 

This guideline targets curators and data providers interested in the representation of causality in molecular interactions and biological systems, but also tool developers, text miners to know what type of information can be expected when dealing with causal statements.


## Introduction to causal statements

A causal statement is a directed interaction between biological entities where the *source entity* (regulator) regulates and has an influence on the activity or the quantity of a *target entity* (regulated entity). The *causal interaction* can be direct (without intermediates) or indirect (the causal impact of *source entity* is transmitted to the *target entity* by a third).
Consequently, the core of a causal statement is composed of three type of elements: the *source entity*, the *causal interaction* (representing the regulation) and the *target entity*. 

![Causal statement](https://github.com/vtoure/MICAST/blob/master/images/causalStatement.svg)

Furthermore, one big challenge relies on capturing enough contextual information to gradually define boundaries under which a specific causal statement is true. This type of information may be diffuse and difficult to curate. With this guideline, we hope to formalise the depiction of that context for a given causal statement in order to obtain contextualised causal statements that can be used for many applications in systems biology and systems medicine.


## The pyramid of causal statement
We split these contextual information into different levels of importance and requirement to give a clear cut of the categories of information.
![Pyramid of causal statement](https://github.com/vtoure/MICAST/blob/master/images/pyramidCausalStatement.svg)

From the most important to the least important layer of information we have:
- MICAST stands for Minimal Information about  a Causal Statement: this is the core of a Causal Statement, the mandatory layer of information
- CONDITION reflects necessary constraints under which the causal statement applies or has been observed
- QUALITY provides information for the user to assess his/her trust on this specific causal statement
- AUXILIARY DATA indicate additional information that provides mechanistic details about the causality in question.


Each layer of the pyramid defines terms that will be detailed in the sections below. For each term, recommendations on ontologies and controlled vocabularies to use are suggested. We strongly advise to follow the recommendations. 

## Notation conventions

We follow the conventions of the [RFC keywords](https://tools.ietf.org/html/rfc2119) to indicate the requirement levels:
* __MUST__ : absolute requirement for a causal statement
* __SHOULD__ : can be ignored in particular circunstances, otherwise required for a causal statement when adequate




## MICAST 
In the MICAST level, a causal statement contains a Source Entity, a Target Entity and a Regulation

Thus we define an object  __Entity__  can either be a source (the regulator) or a target (the regulated). The nature (source or target) of the entity has to be explicit.

### Entity Identifier (MUST)
Unique identification number specifying the exact biological entity involved.

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
The type of regulation exerced by the source entity upon the target entity.  

Ontology recommendation: 
* [Molecular Interaction](https://www.ebi.ac.uk/ols/ontologies/mi/terms?iri=http%3A%2F%2Fpurl.obolibrary.org%2Fobo%2FMI_2234)
*  [Relation Ontology](https://www.ebi.ac.uk/ols/ontologies/ro/properties?iri=http%3A%2F%2Fpurl.obolibrary.org%2Fobo%2FRO_0002506).

### Type (SHOULD)
The biological type of the entity involved (e.g, gene, RNA, mRNA, protein, chemical, phenotype, etc). 

Ontology recommendation: [Molecular Interaction Controlled Vocabulary](https://www.ebi.ac.uk/ols/ontologies/mi) - branch  [interactor type](https://www.ebi.ac.uk/ols/ontologies/mi/terms?iri=http%3A%2F%2Fpurl.obolibrary.org%2Fobo%2FMI_0313)

Note: this information can be useful to distinguish complexes and families.



## CONDITION

### State (SHOULD)
Information about the state of the source or the target necessary for the causal regulation to occur (e.g, the source should be phosphorylated at residue XXX in position YYY to up-regulate the target). Recommendation to come.

## Experimental condition (SHOULD)
A particular experimental setup of an Entity that can explain the causal character of the interaction. For example, an overexpression of a gene.

Ontology recommendation:  [Evidence & Conclusion Ontology](http://www.evidenceontology.org/).

### Species (SHOULD)
Type of species where the causal interaction is observed. In some cases, this information can be implicitly defined from the entity's identifier. 

Ontology recommendation: [Taxonomy ID](https://www.ncbi.nlm.nih.gov/taxonomy) from NCBI.

Note: this information is implicitely present in the Entity's Identifier for most cases (Uniprot ids, Ensembl ids, etc).

### Cell Line, Tissue or Cell Type (SHOULD)
Cell line where the causal interaction is observed or, tissue or cell type where the causal interaction occurs.

Ontology recommendation:
* [BRENDA](https://www.brenda-enzymes.org/ontology.php?ontology_id=3)
* [Cell Ontology](http://www.obofoundry.org/ontology/cl.html) 
* [Uberon](http://uberon.github.io/) 
See discussions  [#5](https://github.com/vtoure/MICAST/issues/5).

### Localisation (SHOULD)
Description of the localisation of the causal interaction: where does the regulation happens? The causal interaction can occur inside a cell or between two cells. 

Ontology recommendation:  [Gene Ontology Cellular Component](http://geneontology.org/) (GO:CC).


## QUALITY

### Evidence (MUST)
The Evidence states how the existence of the causal interaction has been proved (e.g, experimental technique, literature curation, computational method, etc). This information helps the user of the data to know how to trust this causal statement. 

Ontology recommendation:  [Evidence & Conclusion Ontology](http://www.evidenceontology.org/)

### Reference (SHOULD)
Publication identifier in which the causal statement has been highlighted. This is a quality assessment term. We recommend to provide the pubmed ID. It could also be a list of references, in that case, separate the different pubmed IDs with a vertical bar "|".

Ontology recommendation: [PubMed ID](https://www.ncbi.nlm.nih.gov/pmc/pmctopmid/)


## AUXILIARY DATA
Auxiliary data represent for now mechanisms details about the causal statement. Two terms are suggested: Activity and Mechanism. Both terms are complementary, but Activity adds more information because the Target Entity's activity is also highlighted.


### Activity (SHOULD)
The molecular function that is involved in the causal interaction: meaning the function of the entity that causes the regulation  (Source Entity) or that is regulated (Target Entity). Activity is thus a child term of Entity. 

Ontology recommendation: [Gene Ontology Molecular Function](http://geneontology.org/) (GO:MF). 
To be further discussed, see issue [#3](https://github.com/vtoure/MICAST/issues/3).

### Mechanism (SHOULD)
The modification that happens to the target __Entity__ (e.g, phosphorylation, binding, etc).  

Ontology recommendation:
* [Molecular Interaction Controlled Vocabulary](https://www.ebi.ac.uk/ols/ontologies/mi) - branch [causal interaction](https://www.ebi.ac.uk/ols/ontologies/mi/terms?iri=http%3A%2F%2Fpurl.obolibrary.org%2Fobo%2FMI_2233)
* [Molecular Interaction Controlled Vocabulary](https://www.ebi.ac.uk/ols/ontologies/mi) - branch [interaction type](https://www.ebi.ac.uk/ols/ontologies/mi/terms?iri=http%3A%2F%2Fpurl.obolibrary.org%2Fobo%2FMI_0190).



## Summary
In this section, we provide a graph summarising the list of terms by highlighting the layer they belong to in the pyramid of causal statement.

## Examples


## Format
In this section, we will provide a list of formats that follows the MICAST guidelines to represent causal statements.


## Contributors
Vasundra Touré ([vasundra.toure@ntnu.no](mailto:vasundra.toure@ntnu.no))

*Please add your name here*
