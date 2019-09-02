#  Example of the regulation of Protein Kinase A catalytic subunit.

This example of protein regulation shows the effects of cAMP on Protein Kinase A (PKA) catalytic subunit.

PKA is a tetramer composed of two regulatory subunits and two catalytic subunits. The activity of PKA resides in its catalytic subunits. The catalytic subunits are active, able to phosphorylate and regulate targets, only when unbound to the regulatory subunits. When cAMP binds to the regulatory subunits of PKA, the catalytic subunits dissociate with the regulatory subunits.  



<p align="center">
  <img src="https://github.com/vtoure/MI2CAST/blob/master/images/pka.svg" alt="PKA regulation"/>
</p>


## Annotation of the causal interaction following MI2CAST

| Term                         | Identifier | Name/Label                                            | Database                          |
|------------------------------|------------|-------------------------------------------------------|-----------------------------------|
| source                       | 17489      | 3',5'-cyclic AMP                                      | ChEBI                             |
| target                       | P17612     | cAMP-dependent protein kinase catalytic subunit alpha (PRKACA) | Uniprot                  |
| regulation sign              | 2236       | up-regulates activity                                 | PSI-MI                            |
| reference                    | 26687711   | "Protein kinase A catalytic subunit... "              | Pubmed                            |
| evidence                     | 0000302    | author statement used in manual assertion             | ECO                               |
| biological activity source   | 0034237    | protein kinase A regulatory subunit binding           | GO:MF                             |
| biological activity target   | 0004672    | protein kinase activity                               | GO:MF                             |
| compartment of interaction   | 0005737    | cytoplasm                                             | GO:CC                             |
| taxon                        | 9606       | Homo sapiens                                          | NCBI taxonomy                     |


## Written explanation of the causal statement
The chemical 3',5'-cyclic AMP has a protein kinase A regulatory subunit binding activity that up-regulates the protein kinase activity of PRKACA in the cytoplasm. This regulation is identified in humans and has been assessed by a curator based on author statement from the following publication: ["Protein kinase A catalytic subunit isoform PRKACA; history, function and physiology" by Turnham and Scott](https://dx.doi.org/10.1016%2Fj.gene.2015.11.052).
