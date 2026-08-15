# CDK4-Inhibitor-Drug-Discovery-Integrated-2D-3D-QSAR-Docking-Virtual-Screening
An end-to-end computational chemistry and drug discovery pipeline designed for identifying novel, highly potent Cyclin-Dependent Kinase 4 (CDK4) inhibitors based on a core pyrido[2,3-d]pyrimidin-7-one scaffold series.

This project integrates structure-based and ligand-based drug design techniques—including 2D/3D Quantitative Structure-Activity Relationship (QSAR) modeling, force-field molecular docking against human CDK4 (PDB ID: 2A8C), and large-scale virtual screening of the ChEMBL database (>5,000 compounds).Key FeaturesDataset Curation & Scaffold Analysis: Uses a specialized dataset of 52 pyrido[2,3-d]pyrimidin-7-one derivatives with experimental $p\text{IC}_{50}$ values and applies Bemis-Murcko scaffold splitting.2D & 3D QSAR Modeling: Computes physicochemical descriptors, 1024-bit Morgan Fingerprints, and 3D conformer geometric/electronic parameters (Asphericity, Radius of Gyration, Spherocity) via RDKit ETKDG v3 and force-field minimization.Rigorous Validation: Evaluated using Leave-One-Out ($Q^2_{\text{LOO}}$) cross-validation, 5-Fold Cross-Validation ($Q^2_{\text{CV}}$), and external test set validation ($R^2_{\text{ext}}$, $\text{RMSE}_{\text{ext}}$, $\text{MAE}_{\text{ext}}$).Target Structure & Docking: Downloads and prepares human CDK4 crystal structure (PDB ID: 2A8C) and performs conformer-based force-field energy minimization scoring using OpenBabel.ChEMBL Virtual Screening: Programmatically queries over 5,000 bioactivity records from ChEMBL via chembl_webresource_client for target CHEMBL301.Multi-Parameter Optimization (MPO): Filters screened molecules against Lipinski's Rule of Five and prioritizes candidates using a composite score combining predicted activity ($p\text{IC}_{50}$) and docking binding energy.Pipeline Workflow 52 Pyrido[2,3-d]pyrimidin-7-ones ──► 2D/3D Descriptors ──► Gradient Boosting QSAR (Q²_LOO & R²_ext Validation)
                                                                             │
 ChEMBL Database (>5,000 Compounds) ──► QSAR Activity Prediction ────────────┼──► MPO Scoring ──► Top 6 Lead Candidates
                                                                             │
 CDK4 Crystal Structure (2A8C)     ──► Molecular Docking & Binding Energy ───┘
Project StructurePlaintext.
├── cdk4_inhibitors.py              # Complete Python script with end-to-end execution
├── CDK4_inhibitors.ipynb           # Colab-ready notebook version
├── dataset_52.csv                  # Curated 52-compound pyrido[2,3-d]pyrimidin-7-one dataset
├── 2A8C.pdb                        # Human CDK4 target crystal structure downloaded from RCSB PDB
├── qsar_performance_diagnostics.png# 4-Panel publication-quality QSAR metric plots
├── top_6_cdk4_leads.svg            # Chemical structure grid visualization of shortlisted lead compounds
└── README.md                       # Repository documentation
Installation & Environment SetupTo run the pipeline locally or on a custom Jupyter environment, install the required dependencies:Bashpip install rdkit scikit-learn pandas numpy matplotlib seaborn openbabel-wheel chembl_webresource_client
Usage1. Google Colab (Recommended)Click the Open In Colab badge above to launch the interactive notebook directly in your browser without local setup.2. Command Line / Local PythonClone the repository and run the main script:Bashgit clone https://github.com/Babakmamnoon/CDK4-Inhibitor-QSAR-Docking.git
cd CDK4-Inhibitor-QSAR-Docking
python cdk4_inhibitors.py
AuthorBabak MamnoonGitHub: @BabakmamnoonLicenseThis project is licensed under the MIT License
