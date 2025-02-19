# NetCF

## Overview
NetCF (Network control strategy for identifying a Core switching circuit in cell state transition through Feedback analysis) is a framework for identifying a combination target and unraveling the underlying mechanism using Boolean network model.

We also provide the [Core Switching Circuit algorithm](https://github.com/yena2bell/CoreSwitchingCircuit).

## A quick guide on how to use NetCF


## The NetCF consists of three steps: 
### **Step1. Construction of logical dynamic network**

If a user has transcriptome data (e.g., bulk RNA-seq), a logical model is constructed by NetCF as follows (optional):
1.	Data analysis by VIPER : identify a list of key molecules (Notebook1) 
2.	CARNIVAL : infer the network structure (https://github.com/saezlab/CARNIVAL)
3.	Refine logics by modifying the structure and analyzing input-output relationship (Notebook2, Notebook3)

> #### Notebook 1
> The output of Notebook 1 is used as the CARNIVAL input to infer the network structure of interest.
> We also suggest other methods to infer the network structure:
> - Prior knowledge-based construction
> - Data mining construction (e.g., thresholding the regulations by importance score)
> - Correlation-based construction (e.g., Pearson) with established markers

> #### Notebook 2 and 3
> We first define the logic form as "(A1 and A2 and A3 and A4 and ...) and not (R1 or R2 or R3 or ...)", where node A has an activation edge, while node R has an inhibition edge. However, some regulatory interactions or nodes need to be  manually adjusted to accurately capture cellular dynamics based on literature. After modifying a specific logic, to understand the impact of altered conditions on the network system, we conduct a qualitative analysis of individual input-output relationships. Notebook3 has already been provided in [GitHub](https://github.com/namheee/rEMT). 
> - This process continues until the logical model recapitulates cellular behavior. 
> - The output of Notebook 2 and 3 is a logical model with the BoolNet format.

### **Step2. Identification of combination targets based on attractor landscape analysis**
A logical model is given, we identify target candidates and a combination target with core switching circuit by NetCF. Attractor landscape analysis involves examining the attractors, where the network state converges following the model dynamics. From the attractors obtained through attractor simulations, average node activity profiles and phenotype scores for each perturbation are calculated. Notebook 4 provides an example of analyzing attractor landscape.

> #### Notebook 4
> We use BoolNet (R package) for analysis of Boolean network models. Please make sure you have the correct version of R (>4.2).
> - The input of Notebook 4 is a logical model with the BoolNet format. 
> - The output of Notebook 4 is average node activity profiles and phenotype scores as the .csv format.

### **Step3. Mechanism analysis through a core switching circuit**
If there is a combination target to achieve a desired phenotype, the underlying mechanism by regulating the identified combination target is explored based on the core switching circuit, a concept proposed by our study.

> #### Please follow the steps described in tutorials from the [Core Switching Circuit algorithm](https://github.com/yena2bell/CoreSwitchingCircuit)

