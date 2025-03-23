**Monoamine Oxidase A (MAO-A)** is an enzyme that breaks down neurotransmitters such as serotonin, dopamine, and norepinephrine by catalyzing their oxidative deamination. It plays a crucial role in regulating mood and emotional responses. MAO-A inhibitors are used in some antidepressant and neuropsychiatric treatments. <br>  

## **Project Goal** <br>  
The main goal of this project is to evaluate the chemical structures of MAO-A targeting drugs and their functionality. <br>  

## **Project Breakdown** <br>  

### **Part 1: MAO_CDD_ML_Part_1_bioactivity_data.ipynb** <br>  
- **Downloaded and preprocessed** raw bioactivity data from ChEMBL. <br>  
- **Categorized compounds** as **"active," "inactive," or "intermediate"** based on IC50 values. <br>  

### **Part 2: MAO_CDD_ML_Part_2_Exploratory_Data_Analysis_pynb.ipynb** <br>  
- **Conducted ADME analysis** (Absorption, Distribution, Metabolism, Excretion) using the RDKit toolkit by **calculating Lipinski descriptors and pIC50 values** to compare and evaluate the pharmacokinetic properties of active and inactive MAO-A targeting drugs. <br>  
- **Used the Mann-Whitney U test** to compare the distributions of two independent groups (**active vs. inactive** drugs) and determine which descriptor plays a key role in distinguishing its bioactivity. <br>  

### **Part 3: MAO CDD-ML-Part-3-Descriptor-Dataset-Preparation.ipynb** <br>  


