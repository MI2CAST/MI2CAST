# Information content of molecular causal statements
The Minimum Information about a Molecular Interaction Causal Statement (MI2CAST) guidelines describe the minimum and necessary information to depict causal interactions in molecular biology, as well as contextual details. The aim is to homogenize their representation for better usability and understanding, by making the data “FAIR” (Findable, Accessible, Interoperable and Reproducible).

These guidelines target:
* biological curators on the information content to provide when curating a molecular causal interaction,
* biological experimentalists to assess a list of criteria to better contextualize causal interactions,
* causal interactions' data users (modellers, tool developers) to be aware of the type of information that can be expected.


## Introduction to causal statements
The core of a causal statement is composed of three elements: the *source entity*, the *causal interaction* and the *target entity*. It is a directed (i.e., oriented) interaction between biological entities where a *source entity* (regulator) influences the activity of a *target entity* (regulatee). The *causal interaction* can be direct (without intermediates) or indirect (the causal effect of *source entity* is transmitted to the *target entity* by a third).

<p align="center">
  <img src="https://github.com/MI2CAST/MI2CAST/blob/master/images/causalStatement.svg" alt="causal statement"/>
</p>

One big challenge relies on capturing enough contextual information to enrich and disambiguate a causal statement. This type of information may be diffuse and difficult to curate. With these guidelines, we hope to formalize the depiction of that metadata to generate contextualized causal statements that can be used properly for applications in systems biology and systems medicine.


## The MI2CAST rules
MI2CAST defines four main rules:
- __Rule 1__: The source and target entities must be specified
- __Rule 2__: The effect of the interaction must be specified
- __Rule 3__: The provenance and evidence types of the annotation must be specified
- __Rule 4__: The defining contextual details should be specified


>Note: In Rule 4, specific terms are advised to be annotated whenever the data is available and relevant for the causal interaction to occur. For each term, recommendations on ontologies and controlled vocabularies to use are suggested.


### Entity: source and target entity of the causal statement (mandatory)
A unique identifier must be provided to identify the specific biological entity involved in the causal statement.  
A causal statement has at least one source entity and one target entity.

Ontologies recommendations:
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
* Phenotype: [gene ontology biological process ID](http://www.geneontology.org/)
* Stimulus: To be discussed, see issue [#2](https://github.com/vtoure/MICAST/issues/2).

<p align="center">
  <img src="https://github.com/MI2CAST/MI2CAST/blob/master/images/identifiers.svg" alt="identifiers recommendation"/>
</p>

> Note: This list does not preclude the use of other identifiers, as long as appropriate ones are provided.

### Effect of the causal statement (mandatory)
The effect corresponds to the regulatory outcome exerted by the source entity upon the target entity. In general, it can correspond to an increase or decrease of the target.

Ontology recommendation: 
* [Molecular Interaction](https://www.ebi.ac.uk/ols/ontologies/mi/terms?iri=http%3A%2F%2Fpurl.obolibrary.org%2Fobo%2FMI_2234)
* [Relation Ontology](https://www.ebi.ac.uk/ols/ontologies/ro/properties?iri=http%3A%2F%2Fpurl.obolibrary.org%2Fobo%2FRO_0002506).


### Provenance and evidence type of the causal statement (mandatory)
The provenance of the causal statement corresponds to the reference to scientific reports and provides data consumers information about the quality of an annotation: In which publication this causal relationship has been found? 

The evidence type corresponds to experiment or any data the causal interaction is based: How was the causal interaction proven and generated?

#### Reference
The reference relates to either a publication where the causal statement is extracted from. If a combination of publications led to the creation of the causal interaction, then the list of articles must be provided.

Ontology recommendation: 
* [PubMed ID](https://www.ncbi.nlm.nih.gov/pmc/pmctopmid/)
* [DOI](https://www.doi.org/) in the case of articles not reference in MEDLINE (e.g., articles from preprint servers).

#### Type of evidence
The evidence describes how the causal statement has been annotated and has been assessed (e.g., specific experimental procedure, literature curation, computational inference, etc). This information helps the user to evaluate the causal statement. The evidence can be a combination of multiple ones (e.g., a causal interaction assessed from the necessary combination of an author statement and the results of an experiment). The annotation of the evidence type should be as specific as possible

Ontology recommendation:  
* [Evidence & Conclusion Ontology](http://www.evidenceontology.org/).

##### Experimental setup (optional)
If the type of evidence is an experiment, the experimental setup corresponds to a particular experimental conditions supporting the experiment. It specifies the design of the two entities (e.g., overexpression of the source entity).

Ontology recommendation:  
* [Evidence & Conclusion Ontology](http://www.evidenceontology.org/)
* [Molecular Interaction Controlled Vocabulary](https://www.ebi.ac.uk/ols/ontologies/mi) - branch [experimental preparation](https://www.ebi.ac.uk/ols/ontologies/mi/terms?iri=http%3A%2F%2Fpurl.obolibrary.org%2Fobo%2FMI_0346).


### Defining contextual details of the causal statement (optional)
The context informs about the necessary circumstances or observed conditions under which the source entity, the target entity or the causal interaction need to comply with for the causal statement to occur. Every single contextual information in Rule 4 is not necessarily always available for all causal statements. Consequently, only the known and relevant contextual information for a causal statement should be annotated.  

#### Biological activity or biological mechanism
The biological activity corresponds to the molecular activity of the entity causing the regulation or that is regulated (e.g., kinase activity, binding activity). If this information is not available, the biological mechanism of the causal statement that constitutes the biological effect of the source entity on the target entity (e.g., the source entity phosphorylates the target entity which increases the target's activity) should be provided, if available.

When the biological mechanism involves a change in the state of the target, the __modified residue__ and its __position__ may be captured (see [Biological modification](#biological-modification)). This can help in understanding which biological activity of the target is affected by the causal effect.   

Ontology recommendation: 
* [Gene Ontology Molecular Function](http://geneontology.org/) (GO:MF) for the biological activity,
* [Molecular Interaction Controlled Vocabulary](https://www.ebi.ac.uk/ols/ontologies/mi) - branch [causal interaction](https://www.ebi.ac.uk/ols/ontologies/mi/terms?iri=http%3A%2F%2Fpurl.obolibrary.org%2Fobo%2FMI_2233) for the biological mechanism,
* [Molecular Interaction Controlled Vocabulary](https://www.ebi.ac.uk/ols/ontologies/mi) - branch [interaction type](https://www.ebi.ac.uk/ols/ontologies/mi/terms?iri=http%3A%2F%2Fpurl.obolibrary.org%2Fobo%2FMI_0190) for the biological mechanism.


#### Biological type
The biological type of the entity corresponds to the biological nature of the entity (e.g., gene, protein, complex, family, etc) and it should be provided only when the entity's identifier does not correspond to the type of the entity truly annotated. For instance, a publication mentions a transcript but there is no identifier provided of the specific transcript. The curator can then annotate the entity with a gene identifier and specify the biological type as "transcript".

Ontology recommendation: [Molecular Interaction Controlled Vocabulary](https://www.ebi.ac.uk/ols/ontologies/mi) - branch  [interactor type](https://www.ebi.ac.uk/ols/ontologies/mi/terms?iri=http%3A%2F%2Fpurl.obolibrary.org%2Fobo%2FMI_0313).

#### Biological modification
The biological modification corresponds to the physical state of an entity prior to the causal regulation that is needed to observe the causality (e.g., the source entity is phosphorylated at residue XXX in position YYY which enables the increase of the target).

To represent the biological modification, we recommend to represent:
* the modification type (e.g., phosphorylation of a protein, methylation of a gene) using [PSI-MOD](https://www.ebi.ac.uk/ols/ontologies/mod) for proteins, the [SO](http://www.sequenceontology.org/) for genes
* the modified residue, if known, using [ChEBI](https://www.ebi.ac.uk/chebi/)
* the position of the modification with a number indicating the protein sequence position of the modified residue, if known.


#### Taxon
The taxon corresponds to the organism where the causal regulation has its native function and is usually defined through the entity's identifier. In case of heterologous system assays, each entity needs to be annotated with its species of origin.

Ontology recommendation: [Taxonomy ID](https://www.ncbi.nlm.nih.gov/taxonomy) from NCBI.

#### The location of the causal interaction or the entity
The physical location corresponds to the precise localization where a causal interaction is observed or an entity is located. Different levels of locational definitions from the highest level being the tissue type to the most detailed level being the cellular component can be annotated.


##### Tissue type
The tissue type where the causal interaction occurs.

Ontology recommendation: 
* [BRENDA](https://www.brenda-enzymes.org/ontology.php?ontology_id=3)
* [Uberon](https://uberon.github.io/) which covers also body parts and organs
* [Plant Ontology](http://planteome.org/) for plants,
* [Fungal Anatomy Ontology](https://github.com/obophenotype/fungal-anatomy-ontology) for fungi.

##### Cell type or cell line
The cell type  or cell line where the causal interaction is observed.

Ontology recommendation for cell type:
* [Cell Ontology](http://www.obofoundry.org/ontology/cl.html)
* [BRENDA](https://www.brenda-enzymes.org/ontology.php?ontology_id=3)

Ontology recommendation for cell line:
* [Cellosaurus](https://web.expasy.org/cellosaurus/) for cell line
* [BRENDA](https://www.brenda-enzymes.org/ontology.php?ontology_id=3)

##### Cellular component
The cellular component corresponds to the cellular localization (or compartment) where the interaction occurs if one compartment is involved or where the entities are located if multiple compartments are involved. When describing a translocation of a target entity into another compartment, the entity’s original location should be annotated. The entity’s new location could be conveyed by a translocation mechanism term (in [biological mechanism](#biological-activity-or-biological-mechanism); e.g., ‘import into nucleus’ (GO:0051170)).

Ontology recommendation:  [Gene Ontology Cellular Component](http://geneontology.org/) (GO:CC).


## Summary
The following graph provides an overview of the list of terms requested to be checked in MI2CAST:

<p align="center">
  <img src="https://github.com/MI2CAST/MI2CAST/blob/master/images/mi2cast.svg" alt="MI2CAST terms"/>
</p>


## MI2CAST Supports
In this section, we will provide a list of formats or tools that support the concepts defined in the MI2CAST guidelines to represent causal statements.

### causalBuilder

Interface for the curation of causal statements  
causalBuilder website: [https://vtoure.github.io/causalBuilder/](https://vtoure.github.io/causalBuilder/)


