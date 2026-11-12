# Open Food Facts Exploratory Analysis

OpenClassrooms Data Scientist program, Project 3 (2022).

This project cleans and explores Open Food Facts product data to inform a
public health application concept. The notebook examines missing values
and nutrient distributions, uses principal component analysis (PCA), and
compares an experimental composite score with the historical French
nutrition score.

## Project files

- [Data cleaning and exploratory analysis notebook](Bouhbel_Khalid_1_nettoyage_et_exploration_092022.ipynb)
- [Original project presentation (PDF, in French)](Bouhbel_Khalid_2_presentation_092022.pdf)
- [PCA plotting helpers](functions.py)

## Run the notebook

Place a compatible tab-separated Open Food Facts export at
`Data/fr.openfoodfacts.org.products.csv`. The notebook ran end to end
with a historical export whose ZIP entry is dated 2017. The exact export
used for the 2022 presentation could not be confirmed. The recent export
checked for this project lacks legacy fields including
`nutrition-score-fr_100g` and `ingredients_from_palm_oil_n`.

From the repository root, create the environment and run the notebook:

```bash
conda create -y -n projet3 --override-channels -c conda-forge \
  python=3.11 nbconvert ipykernel pandas numpy matplotlib seaborn \
  scipy scikit-learn statsmodels

conda run --no-capture-output -n projet3 \
  python -m nbconvert --to notebook --execute --stdout \
  --ExecutePreprocessor.kernel_name=python3 \
  --ExecutePreprocessor.timeout=1800 \
  Bouhbel_Khalid_1_nettoyage_et_exploration_092022.ipynb > /dev/null
```

## Reproduction note

K-nearest-neighbor imputation uses three neighbors from a fixed reference
sample of up to 2,000 products (`random_state=42`). The resulting scores
may differ from those in the original presentation.
