This is the tutorial for the aiida-yambo plugin (and a little bit for aiida-yambo-wannier90 one).

Supported calculations: HF, GW, BSE, IP-RPA optics.
Features: automated workflows, QP merging, Wannier90 interface.

The tutorial is structured in jupyter notebook, interactive python shells.
Prerequisite: AiiDA tutorial: https://aiida-tutorials.readthedocs.io/en/latest/
            
The tutorial supposes that you already have all codes and computer set up in your installation. 

(A) Brief pre-requisites instructions:

	(01_structures_and_pseudos) We introduce how to parse structures from quantumespresso files and store them as 
	StructureData, to then be used in our calculations.  Then, we introduce how to store in the AiiDA database the pseudopotentials within the aiida-pseudo plugin.


(B) Run aiida-yambo plugin!
	
	(1) YamboCalculation: simple/bare Yambo
		(1.1) how to inspect outputs
