# Formalising the representation of causal statements
The MI2CAST (Minimum Information about a Molecular Interaction causal statement) guideline describes information that is necessary to depict causal interactions in molecular biology. The aim is to homogeneise their representation for a better usability and understanding, by making the data “FAIR” (Findable, Accessible, Interoperable and Reproducible).

This guideline targets curators and data providers of causality in molecular interactions and biological systems, but also tool developers, text miners to know what type of information can be expected when dealing with causal statements.


## Introduction to causal statements
A causal statement is a directed interaction between biological entities where a *source entity* (regulator) regulates and has an influence on the activity or the quantity of a *target entity* (regulatee). The *causal interaction* can be direct (without intermediates) or indirect (the causal impact of *source entity* is transmitted to the *target entity* by a third).

The core of a causal statement is composed of three elements: the *source entity*, the *causal interaction* (representing the regulation) and the *target entity*. 

<p align="center">
  <img src="https://github.com/vtoure/MI2CAST/blob/master/images/causalStatement.svg" alt="causal statement"/>
</p>

Furthermore, one big challenge relies on capturing enough contextual information to gradually enrich a causal statement and define boundaries under which it is true. This type of information may be diffuse and difficult to curate. With this guideline, we hope to formalise the depiction of that metadata in order to obtain contextualised causal statements that can be used for applications in systems biology and systems medicine.


## The MI2CAST rules
MI2CAST defines four main rules to be followed when annotating a molecular interaction causal statement:
- Rule 1: The source and target entities of a causal interaction must be specified
- Rule 2: The regulation sign of a causal interaction must be specified
- Rule 3: The quality of a causal interaction should be specified
- Rule 4: The available context about a causal interaction should be specified

In addition to the rules, specific terms are advised to be annotated when the data is available. For each term, recommendations on ontologies and controlled vocabularies to use are suggested. We strongly advise to follow the recommendations.


### Entity
A unique identifier helps to identify the specific biological entity involved in the causal statement.
A causal statement has at least one source entity and one target entity.

We recommend to use different ontologies depending on the type of the biological entity:
* Gene: [ensembl gene ID](http://www.ensembl.org), [Entrez gene ID](https://www.ncbi.nlm.nih.gov/gene)
* RNA (non coding): [rna central ID](http://rnacentral.org/)
* mRNA: 
  * Recommended: [ensembl transcript ID](http://www.ensembl.org)
  * Alternative: [ensembl gene ID](http://www.ensembl.org)
* Protein: [uniprot ID](http://www.uniprot.org/)
* Chemical: 
  * Recommended: [chebi ID](https://www.ebi.ac.uk/chebi/)
  * Alternative: [pubchem ID](https://pubchem.ncbi.nlm.nih.gov/)
* Family: list of string of IDs following the rules (for a family of genes, use ensembl gene ID or Entrez gene ID, for a family of proteins, use uniprot IDs, etc).
* Complex:
  * For stable complex: [complexportal ID](https://www.ebi.ac.uk/complexportal/home)
  * For transient complex: list of string of the components of the complex.
* Phenotype: [gene ontology ID](http://www.geneontology.org/)
* Stimulus: To be discussed, see issue [#2](https://github.com/vtoure/MICAST/issues/2).

### Regulation
The type of regulation exerced by the source entity upon the target entity in the causal statement. For instance, an up-regulation or a down-regulation.

Ontology recommendation: 
* [Molecular Interaction](https://www.ebi.ac.uk/ols/ontologies/mi/terms?iri=http%3A%2F%2Fpurl.obolibrary.org%2Fobo%2FMI_2234)
* [Relation Ontology](https://www.ebi.ac.uk/ols/ontologies/ro/properties?iri=http%3A%2F%2Fpurl.obolibrary.org%2Fobo%2FRO_0002506).


### Quality
The confidence level provides information about the assessment and the provenance of the causal statement: In which publication this causal relationship has been found? What the causal interaction manually curated or automatically generated?
This provides some criteria to rank a causal statement.

#### Reference
Publication or combination of publications that led to the creation of a causal interaction.

Ontology recommendation: [PubMed ID](https://www.ncbi.nlm.nih.gov/pmc/pmctopmid/).

#### The evidence
How does the causal statement has been annotated (e.g., experimental procedure, literature curation, computational inference, etc)? This information helps the user of the data to know how to trust this causal statement.

Ontology recommendation:  [Evidence & Conclusion Ontology](http://www.evidenceontology.org/)


### CONTEXT
The context informs about necessary circumstances under which a causal statement has been observed or proven to be true.

#### Biological activity or mechanism
The molecular function of the entity, meaning the function of the entity that causes the regulation or that is regulated (e.g., kinase activity). Otherwise, the mechanism of the causal statement that constitutes the biological effect on the target entity (e.g., phosphorylation, binding, etc).

Ontology recommendation: 
* [Gene Ontology Molecular Function](http://geneontology.org/) (GO:MF) for the biological activity,
* [Molecular Interaction Controlled Vocabulary](https://www.ebi.ac.uk/ols/ontologies/mi) - branch [causal interaction](https://www.ebi.ac.uk/ols/ontologies/mi/terms?iri=http%3A%2F%2Fpurl.obolibrary.org%2Fobo%2FMI_2233) for the biological mechanism,
* [Molecular Interaction Controlled Vocabulary](https://www.ebi.ac.uk/ols/ontologies/mi) - branch [interaction type](https://www.ebi.ac.uk/ols/ontologies/mi/terms?iri=http%3A%2F%2Fpurl.obolibrary.org%2Fobo%2FMI_0190) for the biological mechanism.


#### Biological type
The biological type of the entity involved (e.g., gene, protein, chemical, complex, family, etc).

Ontology recommendation: [Molecular Interaction Controlled Vocabulary](https://www.ebi.ac.uk/ols/ontologies/mi) - branch  [interactor type](https://www.ebi.ac.uk/ols/ontologies/mi/terms?iri=http%3A%2F%2Fpurl.obolibrary.org%2Fobo%2FMI_0313).

#### Biological modification
Information about the modification of the source or the target entity necessary for the causal regulation to occur (e.g., the source should be phosphorylated at residue XXX in position YYY to up-regulate the target).
For proteins we recommend to annotate:
* the modification type (e.g., phosphorylation of a protein, methylation of a gene or RNA) for which we recommend using [PSI-MOD](https://www.ebi.ac.uk/ols/ontologies/mod) for proteins , the [SO](http://www.sequenceontology.org/) for genes
* the modified residue, if known, using [ChEBI](https://www.ebi.ac.uk/chebi/)
* the position of the modification with a number indicating which residue is modified, if known
 


#### Compartment
The cellular localization of the entities or the causal regulation. The causal interaction can occur inside a cell or between two cells. 

Ontology recommendation:  [Gene Ontology Cellular Component](http://geneontology.org/) (GO:CC).

#### Taxon
Type of taxon where the causal regulation is observed. 
Taxon can also refer to the organism of the source or target entity to distinguish causality assessed with entities from different taxons. In some cases, the taxon information is implicitly defined in the Entity's identifier. 

Ontology recommendation: [Taxonomy ID](https://www.ncbi.nlm.nih.gov/taxonomy) from NCBI.

#### Cell Line, Tissue or Cell Type
Cell line where the causal statement is observed or, tissue or cell type where the causal interaction occurs. 

Ontology recommendation:
* [BRENDA](https://www.brenda-enzymes.org/ontology.php?ontology_id=3)
* [Cell Ontology](http://www.obofoundry.org/ontology/cl.html) 
* [Uberon](http://uberon.github.io/) 
See discussions  [#5](https://github.com/vtoure/MICAST/issues/5).


#### Experimental setup
A source or target entity can be represented by a specific experimental setup which could explain the causal character of the causal statement. For example, an overexpression of a gene.

Ontology recommendation: 
* [Molecular Interaction Controlled Vocabulary](https://www.ebi.ac.uk/ols/ontologies/mi) - branch [experimental preparation](https://www.ebi.ac.uk/ols/ontologies/mi/terms?iri=http%3A%2F%2Fpurl.obolibrary.org%2Fobo%2FMI_0346)
* [Evidence & Conclusion Ontology](http://www.evidenceontology.org/).

## Summary
The following graph provides an overview of the list of terms requested to be checked in MI2CAST.

<p align="center">
  <img src="https://github.com/vtoure/MI2CAST/blob/master/images/mi2cast.svg" alt="MI2CAST terms"/>
</p>



## MI2CAST Supports
In this section, we will provide a list of formats or tools that support the MI2CAST guidelines to represent causal statements.


