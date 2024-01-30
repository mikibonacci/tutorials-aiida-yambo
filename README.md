# `aiida-yambo` and `aiida-yambo-wannier90` tutorial: automation of Green's function methods

This repository contains a collection of jupyter notebook which are meant to be a tutorial on how to run the `aiida-yambo` and `aiida-yambo-wannier90` plugin for the AiiDA platform. 

#### Structure of the tutorial:

- tutorials-aiida-yambo/prerequisites: 
    - [AiiDA prerequisite](prerequisites/0_1_structure_and_pseudos.ipynb): how to set up structures, pseudopotentials and groups in AiiDA;
    - [aiida-quantumespresso prerequisite](prerequisites/0_2_QE_starting_point.ipynb): how to run the required DFT starting point, via the `aiida-quantumespresso` plugin;
- tutorials-aiida-yambo/yambo:
    - [Simple yambo calculation](yambo/1_YamboCalculation_G0W0.ipynb);
    - [Enabling error handling](yambo/2_YamboRestart_G0W0.ipynb);
    - From scratch to yambo results: DFT+MBPT
        - [One G0W0 calculation](yambo/3_1_YamboWorkflow_G0W0.ipynb);
        - [Multiple QP calculations](yambo/3_2_YamboWorkflow_QP.ipynb);
        - [A BSE simulation using scissor&stretching corrections](yambo/5_1_YamboWorkflow_BSE.ipynb);
        - [A BSE simulation using explicit quasiparticle corrections](yambo/5_2_YamboWorkflow_BSE_QP.ipynb);
    - Automated convergence of MBPT:
        - [G0W0 case](yambo/4_YamboConvergence_G0W0.ipynb);
        - [BSE case](yambo/6_YamboConvergence_BSE.ipynb);
- tutorials-aiida-yambo/yambo_wannier90: interpolating band structures
    - [W90@QE](yambo_wannier90/1_Band_interpolation_W90_DFT.ipynb);
    - [reference QE band structure](yambo_wannier90/2_PwBands.ipynb);
    - [Fully automated W90@G0W0 interpolated band structure](yambo_wannier90/3_Band_interpolation_W90_G0W0_full.ipynb)
    - [Analysis of W90@G0W0](yambo_wannier90/hBN_analysis.ipynb).

#### Prerequisites:

- AiiDA
- `aiida-quantumespresso`