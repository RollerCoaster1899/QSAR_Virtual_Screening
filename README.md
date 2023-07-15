# QSAR_Virtual_Screening

QSAR Model generation based on ChemBL target and virtual screening based on Zinc "World" subset using molecular fingerprints.

QSAR Model generation

The given code represents a series of functions and code snippets related to generating a QSAR (Quantitative Structure-Activity Relationship) model and evaluating molecules using the model. Here's a brief explanation of each part:

1. Importing Required Libraries:
   - This part imports the necessary libraries such as `numpy`, `chembl_webresource_client`, `pandas`, `rdkit`, `sklearn`, and `matplotlib`.

2. Function Definitions:
   - `target_retrieval(search)`: Retrieves target information from the ChEMBL database based on a search term.
   - `target_info_retrieval(search)`: Retrieves activity data for a specific target from the ChEMBL database.
   - `build_qsar_model(data)`: Builds a QSAR model using the provided activity data.
   - `evaluate_molecule(mol_smiles, model)`: Evaluates a molecule using the QSAR model and returns the predicted pIC50 value.
   - `plot_predicted_vs_real(y_test, y_pred)`: Plots a scatter plot of predicted pIC50 values versus real pIC50 values.
   - `identify_pharmacophores(feature_importance, fingerprint_columns, threshold)`: Identifies important pharmacophores based on feature importance from the QSAR model.
   - `draw_molecule(smiles)`: Draws a molecule using its SMILES representation.

3. Example Usage:
   - This part demonstrates the usage of the functions to retrieve target information and activity data from the ChEMBL database, build a QSAR model, and evaluate a molecule.

The example usage code retrieves target information and activity data for a target with the ChEMBL ID "CHEMBL2179". It then builds a QSAR model using the activity data and evaluates a molecule represented by the SMILES string "CC(=O)NC1=CC=CC=C1". The predicted pIC50 value for the molecule is printed.

Please note that this code assumes the availability of the ChEMBL database and the required data for building the QSAR model.


Virtual Screening

1. Importing Required Libraries:
   - This part imports the necessary libraries such as `pandas`, `rdkit`, `chembl_webresource_client`, and `matplotlib`.

2. Function Definition:
   - `evaluate_molecule(mol_smiles, model)`: Evaluates a molecule using the QSAR model and returns the predicted pIC50 value. This function is the same as in the previous code.

3. Load Data:
   - The code loads data from a CSV file named 'QSAR-Virtual_Screening_Data.csv' and stores it in a DataFrame named `df`. The actual CSV file path should be provided.

4. Example Molecule Evaluation:
   - The code applies the `evaluate_molecule` function to each molecule in the DataFrame `df['smiles']` column and assigns the predicted pIC50 values to a new column named 'pIC50' in the DataFrame.

5. Sort and Select Top 10:
   - The DataFrame `df` is sorted based on the 'pIC50' column in descending order using `sort_values()`, and the top 10 molecules with the highest potency values are selected and stored in the DataFrame `top_10`.

6. Generate Potency Distribution Plot:
   - The code generates a histogram plot of the predicted pIC50 values from the 'pIC50' column of the original DataFrame `df` using `plt.hist()`. This plot visualizes the distribution of the predicted pIC50 values.

7. Generate Images and Print Molecule Information for Top 10:
   - The code iterates over the rows of the `top_10` DataFrame and generates images for each molecule using the `draw_molecule` function. If an image is successfully generated, it prints the molecule's information, including the SMILES and predicted pIC50 value.

8. Generate Similarity Coefficient Matrix:
   - The code generates a matrix of similarity coefficients between the top 10 molecules. It iterates over each pair of molecules, calculates their similarity using the Tanimoto coefficient, and stores the values in a 2D list `similarity_matrix`. The similarity matrix is then converted into a DataFrame `similarity_df` for better visualization.

9. Print Similarity Coefficient Matrix:
   - The code prints the similarity coefficient matrix `similarity_df`, which shows the pairwise similarity between the top 10 molecules.
