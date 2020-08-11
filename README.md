# MI2CAST
The Minimum Information about a Molecular Interaction Causal Statement (MI2CAST)

This repository contains the guidelines defined for the curation of causal statements in molecular interactions.

## Introduction
A causal statement is defined as an interaction between biological entities (gene, protein, etc) where a source entity regulates the activity of a target entity.

This repository is a community effort to homogenize and categorize information for representing causal relationships. Terms are defined and ontologies/controlled vocabularies to use are suggested for each term.

## Documentation
Access to the full [MI2CAST guidelines](docs/MI2CAST_guideline.md).

### Short summary
MI2CAST is composed of four rules expressing the annotations terms expected to be annotated together with a causal interaction. The following table summarizes for each rule the list of terms recommended in MI2CAST (column 1). In addition, a short definition (column 2) is provided as well as the recommended ontologies and controlled vocabularies to use (column 3). The 'mandatory annotation' column informs if the annotation of the term is mandatory or not. If not, it is indicated in which cases an annotation can be expected.
> Make use of the links to reach web-pages that provide more information.

#### Rule 1: The source and target entities must be specified

|	term |	short definition |	recommended CV/ontology |	mandatory annotation |
|-|-|-|-|
| source entity |	regulator entity |	[case-specific, see doc](https://github.com/MI2CAST/MI2CAST/blob/master/docs/MI2CAST_guideline.md#rule-1-source-and-target-entity-of-the-causal-statement-mandatory)	| yes |
| target entity |	regulated entity |	[case-specific, see doc](https://github.com/MI2CAST/MI2CAST/blob/master/docs/MI2CAST_guideline.md#rule-1-source-and-target-entity-of-the-causal-statement-mandatory)	| yes |

#### Rule 2: The causal relationship of the interaction must be specified

|	term |	short definition |	recommended CV/ontology |	mandatory annotation |
|-|-|-|-|
| causal relationship |	regulatory relationship from source to target |	[MI](https://www.ebi.ac.uk/ols/ontologies/mi/terms?iri=http%3A%2F%2Fpurl.obolibrary.org%2Fobo%2FMI_2234), [RO](https://www.ebi.ac.uk/ols/ontologies/ro/properties?iri=http%3A%2F%2Fpurl.obolibrary.org%2Fobo%2FRO_0002506)	| yes |

#### Rule 3: The provenance and evidence types of the annotation must be specified

|	term |	short definition |	recommended CV/ontology |	mandatory annotation |
|-|-|-|-|
| reference(s) |	publication(s) where the causal interaction has been curated from |	[PubMed](https://www.ncbi.nlm.nih.gov/pmc/pmctopmid/), [DOI](https://www.doi.org/)	| yes |
| type of evidence |	assessement of the causal interaction |	[ECO](http://www.evidenceontology.org/)	| yes |
| experimental setup(s) |	particular experimental setting(s) applied to the entities to observe the causal interaction |	[ECO](http://www.evidenceontology.org/), [MI](https://www.ebi.ac.uk/ols/ontologies/mi/terms?iri=http%3A%2F%2Fpurl.obolibrary.org%2Fobo%2FMI_0346), [OBI](http://obi-ontology.org/)	| if any and known |

#### Rule 4: The defining contextual details should be specified

| term |	short definition |	recommended CV/ontology |	mandatory annotation |
|-|-|-|-|
| biological activity |	molecular function of the entities, involved in the causal interaction |	[GO:MF](http://geneontology.org/)	| if known |
| biological mechanism |	biological process of the causal interaction |	MI ([causal interaction](https://www.ebi.ac.uk/ols/ontologies/mi/terms?iri=http%3A%2F%2Fpurl.obolibrary.org%2Fobo%2FMI_2233) or [interaction type](https://www.ebi.ac.uk/ols/ontologies/mi/terms?iri=http%3A%2F%2Fpurl.obolibrary.org%2Fobo%2FMI_0190) branch)	| if biological activity is unknown |
| biological type | biological nature of the entity | MI ([interactor type](https://www.ebi.ac.uk/ols/ontologies/mi/terms?iri=http%3A%2F%2Fpurl.obolibrary.org%2Fobo%2FMI_0313) branch) | if ambiguous or incorrect from the entity's identifier |
| taxon |	the taxon where the causal interaction is observed or where the entity is from |	[NCBI Taxonomy](https://www.ncbi.nlm.nih.gov/taxonomy)	| if can't be inferred |
| biological modification(s) |	physical configuration(s) or conformation(s) of an entity |	[see doc](https://github.com/MI2CAST/MI2CAST/blob/master/docs/MI2CAST_guideline.md#biological-modification) | if any |
| compartment |	cellular location the causal interaction is observed in or the entity is present | [GO:CC](http://geneontology.org/) | if known |
| tissue type |	the tissue structure with a specific function in which the causal interaction is observed	| [BRENDA](https://www.brenda-enzymes.org/ontology.php?ontology_id=3), [Uberon](https://uberon.github.io/), [PO](http://planteome.org/), [FAO](https://github.com/obophenotype/fungal-anatomy-ontology) |	if known |
| cell line or cell type |	the cell culture or form where the causal interaction is observed or occurs |	[CL](http://www.obofoundry.org/ontology/cl.html), [BRENDA](https://www.brenda-enzymes.org/ontology.php?ontology_id=3), [Cellosaurus](https://web.expasy.org/cellosaurus/) | if known |

## Concrete examples
* [E2F8 (transcription factor) regulation of CCNE1 (target gene) causal statement](examples/TF-TG.md),
* [Protein kinase A catalytic subunit regulation](examples/PKA_regulation.md),
* [Two transcription factors regulating a gene](examples/2TF-TG.md),
* [A miRNA regulating a biological process](examples/mirna_process.md).

### Examples for future applications
* [Cell to cell causal interaction](examples/cell_cell_interaction.md).

## Citation
For citing MI2CAST, please use the following reference:  
Touré, V.; Vercruysse, S.; Acencio, M.L.; Lovering, R.C.; Orchard, S.; Bradley, G.; Casals-Casas, C.; Chaouiya, C.; del-Toro, N.; Flobak, Å.; Gaudet, P.; Hermjakob, H.; Hoyt, C.T.; Licata, L.; Lægreid, A.; Mungall, C.; Niknejad, A.; Panni, S.; Perfetto, L.; Porras, P.; Pratt, D.; Thieffry, D.; Thomas, P.D.; Türei, D.; Saez-Rodriguez, J.; Kuiper, M. The Minimum Information about a Molecular Interaction Causal Statement (MI2CAST).  *Bioinformatics*, 2020, btaa622, [https://doi.org/10.1093/bioinformatics/btaa622](https://doi.org/10.1093/bioinformatics/btaa622)

## Contact 
Vasundra Touré ([vasundra.toure@ntnu.no](mailto:vasundra.toure@ntnu.no))
