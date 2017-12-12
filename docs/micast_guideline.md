# MICAST Guideline

The MICAST guideline describes the minimum information  that is necessary to depict causal interactions in Biology. The aim is to homogeneise the representation of causality within the community to make the data “FAIR” (Findable, Accessible, Interoperable and Reproducible). This guideline targets curators and data providers interested in the representation of causality aspects in molecular interactions and biological systems. 


## Introduction to causality statements

A causality statement is a binary directed interaction between two biological entities where the *source entity* regulates and has an influence on the activity or the quantity of the *target entity*. The *causal interaction* can be direct (without intermediates) or indirect (the causal impact of *source entity* is transmitted to the *target entity* by a third).
Consequently, a causal statement is composed of three type of elements: the *source entity*, the *causal interaction* and the *target entity*. 
We define the object __Entity__ for representing the source and target entities, and the object __Causal Interaction__ for representing the causal interaction.
Furthermore, the challenge of representing causality statements relies on capturing enough contextual information about the elements that compose the causality statement. The context is important to define boundaries under which a specific causal statement is true. We would like to define this as a __Context__ object.

