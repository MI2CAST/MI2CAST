# Information content of molecular causal statements
The MI2CAST (Minimum Information about a Molecular Interaction Causal Statement) guidelines describe information that are necessary to depict causal interactions in molecular biology. The aim is to homogeneize their representation for a better usability and understanding, by making the data “FAIR” (Findable, Accessible, Interoperable and Reproducible).

These guidelines target:
* biological curators on the information content to provide about molecular causal interactions,
* biological experimentalists to assess a list of criteria necessary to contextualize causal interactions,
* tool developers and text miners to know the type of information that can be expected


## Introduction to causal statements
The core of a causal statement is composed of three elements: the *source entity*, the *causal interaction* and the *target entity*. It is a directed interaction between biological entities where a *source entity* (regulator) influences the activity or the quantity of a *target entity* (regulatee). The *causal interaction* can be direct (without intermediates) or indirect (the causal effect of *source entity* is transmitted to the *target entity* by a third).

<p align="center">
  <img src="https://github.com/vtoure/MI2CAST/blob/master/images/causalStatement.svg" alt="causal statement"/>
</p>

Furthermore, one big challenge relies on capturing enough contextual information to gradually enrich a causal statement. This type of information may be diffuse and difficult to curate. With these guidelines, we hope to formalize the depiction of that metadata in order to obtain contextualized causal statements that can be used for applications in systems biology and systems medicine.


## The MI2CAST rules
MI2CAST defines four main rules:
- Rule 1: The source and target entities of a causal interaction must be specified
- Rule 2: The regulation sign of a causal interaction must be specified
- Rule 3: The origin of a causal interaction must be specified
- Rule 4: The available context about a causal interaction should be specified

In addition to the rules, specific terms are advised to be annotated when the data is available. For each term, recommendations on ontologies and controlled vocabularies to use are suggested.


### Entity: source and target entity of the causal statement (mandatory)
A unique identifier must be provided to identify the specific biological entity involved in the causal statement.
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
* Family: 
  * provide a list of members IDs following the rules (for a family of genes, use ensembl gene ID or Entrez gene ID, for a family of proteins, use uniprot IDs, etc)
  * annotate the biological type of the entity as a "[family](http://purl.obolibrary.org/obo/MI_1304)"
* Complex:
  * For stable complex: [complexportal ID](https://www.ebi.ac.uk/complexportal/home)
  * For transient complex: 
    * provide a list of the components of the complex
    * annotate the biological type of the entity as a "[complex](http://purl.obolibrary.org/obo/MI_0314)"
* Phenotype: [gene ontology ID](http://www.geneontology.org/)
* Stimulus: To be discussed, see issue [#2](https://github.com/vtoure/MICAST/issues/2).

<p align="center">
  <img src="https://github.com/vtoure/MI2CAST/blob/master/images/identifiers.svg" alt="identifiers recommendation"/>
</p>


### Regulation sign of the causal statement (mandatory)
The regulation sign exerced by the source entity upon the target entity can correspond to an up-regulation or a down-regulation of a specific activity or the quantity of the target.

Ontology recommendation: 
* [Molecular Interaction](https://www.ebi.ac.uk/ols/ontologies/mi/terms?iri=http%3A%2F%2Fpurl.obolibrary.org%2Fobo%2FMI_2234)
* [Relation Ontology](https://www.ebi.ac.uk/ols/ontologies/ro/properties?iri=http%3A%2F%2Fpurl.obolibrary.org%2Fobo%2FRO_0002506).


### Origin of the causal statement (mandatory)
The origin of the causal statement provides information about the assessment and the provenance of the causal statement: In which publication this causal relationship has been found? How was the causal interaction generated? It provides some criteria to be able to rank a causal statement.

#### Reference
The reference relates to a publication or a combination of publications that allowed the identification of a causal interaction.

Ontology recommendation: 
* [PubMed ID](https://www.ncbi.nlm.nih.gov/pmc/pmctopmid/)
* [DOI](https://www.doi.org/) in the case of articles from preprint servers.

#### Evidence
The evidence describes how the causal statement has been annotated and has been assessed (e.g., specific experimental procedure, literature curation, computational inference, etc). This information helps the user to evaluate the causal statement. The evidence can be a combination of multiple ones (e.g., causal statement manually extracted from a manuscript based on the results of an experiment).

Ontology recommendation:  [Evidence & Conclusion Ontology](http://www.evidenceontology.org/)


### Available context of the causal statement (optional)
The context informs about the necessary circumstances or observed conditions under which the source entity, the target entity or the causal interaction needs to comply with for the causal statement to occur. Every single contextual information in Rule 4 is not necessarily always available for all causal statements. Consequently, only the known and relevant contextual information for a causal statement should be annotated.  

#### Biological activity or biological mechanism
The biological function corresponds to the molecular activity of the entity that is the cause of the regulation or that is regulated (e.g., kinase activity). If this information is not available, the biological mechanism of the causal statement that constitutes the biological effect of the source entity on the target entity (e.g., the source entity phosphorylates the target entity which increases the target's activity) should be provided.

Ontology recommendation: 
* [Gene Ontology Molecular Function](http://geneontology.org/) (GO:MF) for the biological activity,
* [Molecular Interaction Controlled Vocabulary](https://www.ebi.ac.uk/ols/ontologies/mi) - branch [causal interaction](https://www.ebi.ac.uk/ols/ontologies/mi/terms?iri=http%3A%2F%2Fpurl.obolibrary.org%2Fobo%2FMI_2233) for the biological mechanism,
* [Molecular Interaction Controlled Vocabulary](https://www.ebi.ac.uk/ols/ontologies/mi) - branch [interaction type](https://www.ebi.ac.uk/ols/ontologies/mi/terms?iri=http%3A%2F%2Fpurl.obolibrary.org%2Fobo%2FMI_0190) for the biological mechanism.


#### Biological type
The biological type of the entity (e.g., gene, protein, chemical, complex, family, etc) should be provided when the entity's identifier does not correspond to the type of the entity truly annotated. For instance, a publication mentions a transcript but there is no identifier provided of the specific transcript. The curator can then annotate the entity with a gene identifier and specify the biological type as "transcript".

Ontology recommendation: [Molecular Interaction Controlled Vocabulary](https://www.ebi.ac.uk/ols/ontologies/mi) - branch  [interactor type](https://www.ebi.ac.uk/ols/ontologies/mi/terms?iri=http%3A%2F%2Fpurl.obolibrary.org%2Fobo%2FMI_0313).

#### Biological modification
The biological modification corresponds to physical changes of an entity necessary for the causal regulation to occur (e.g., the source entity should be phosphorylated at residue XXX in position YYY to up-regulate the target).

We recommend to annotate:
* the modification type (e.g., phosphorylation of a protein, methylation of a gene) for which we recommend using [PSI-MOD](https://www.ebi.ac.uk/ols/ontologies/mod) for proteins , the [SO](http://www.sequenceontology.org/) for genes
* the modified residue, if known, using [ChEBI](https://www.ebi.ac.uk/chebi/)
* the position of the modification with a number, if known


#### The location of the causal interaction or the entity
The location of the causal interaction or the entity contains different levels of locational definitions from the highest level being the taxon to the most detailed level being the cellular component.

##### Taxon
The taxon corresponds to the organism where the causal regulation has its native function. The taxon can also refer to the organism of the source or the target entity, to be able to distinguish causality assessed with entities from different taxons (heterologous case). Finally, this information can be implicitly defined in the Entity's identifier (Uniprot ID, Ensembl ID). 

Ontology recommendation: [Taxonomy ID](https://www.ncbi.nlm.nih.gov/taxonomy) from NCBI.

##### Tissue type
The tissue type where the causal interaction occurs.

Ontology recommendation: 
* [BRENDA](https://www.brenda-enzymes.org/ontology.php?ontology_id=3)
* [Uberon](https://uberon.github.io/) which covers also body parts and organs.

##### Cell type
The cell type where the causal interaction occurs.

Ontology recommendation:
* [Cell Ontology](http://www.obofoundry.org/ontology/cl.html)
* [BRENDA](https://www.brenda-enzymes.org/ontology.php?ontology_id=3)

##### Cell Line
The cell line where the causal statement is observed. 

Ontology recommendation:
* [Cellosaurus](https://web.expasy.org/cellosaurus/) for cell line
* [BRENDA](https://www.brenda-enzymes.org/ontology.php?ontology_id=3)

##### Cellular component
The cellular component corresponds to the cellular localization (or compartment) where the entities are localized or where the causal interaction occurs. The causal interaction can occur inside a cell or between two cells.

Ontology recommendation:  [Gene Ontology Cellular Component](http://geneontology.org/) (GO:CC).


#### Experimental setup
The experimental setup corresponds to a specific experimental condition used to detect an entity's involvement in a causal statement. For example, the overexpression of a gene.

Ontology recommendation: 
* [Molecular Interaction Controlled Vocabulary](https://www.ebi.ac.uk/ols/ontologies/mi) - branch [experimental preparation](https://www.ebi.ac.uk/ols/ontologies/mi/terms?iri=http%3A%2F%2Fpurl.obolibrary.org%2Fobo%2FMI_0346)
* [Evidence & Conclusion Ontology](http://www.evidenceontology.org/).

## Summary
The following graph provides an overview of the list of terms requested to be checked in MI2CAST:

<p align="center">
  <img src="https://github.com/vtoure/MI2CAST/blob/master/images/mi2cast.svg" alt="MI2CAST terms"/>
</p>


## MI2CAST Supports
In this section, we will provide a list of formats or tools that support the MI2CAST guidelines to represent causal statements.

### causalBuilder

Interface for the curation of causal statements  
causalBuilder website: [https://vtoure.github.io/causalBuilder/](https://vtoure.github.io/causalBuilder/)


