# llm-sf-eval-profile
[![DOI](https://zenodo.org/badge/993305514.svg)](https://doi.org/10.5281/zenodo.15556521)

This repository contains a set of Jupyter notebooks for analyzing evaluation patterns of various Large Language Models (LLMs) on science fiction short stories. The analyses cover score normalization, clustering, statistical testing, and keyword extraction from model comments.

## Overview

| Notebook | Description |
|----------|-------------|
| `Sec_4.1_Z-score.ipynb` | Computes Z-scores per model and session for each story. Visualizes differences across evaluations. |
| `Sec_4.2_Boxplot.ipynb` | Draws boxplots of raw scores per story. Highlights variance to indicate evaluation diversity. |
| `Sec_4.5_PCA.ipynb` | Applies PCA to evaluation scores and outputs eigenvalues and factor loadings. Generates 2D biplots. |
| `Sec_4.6_k-means.ipynb` | Performs KMeans clustering on PCA loadings. Evaluates optimal cluster number with WSS and silhouette scores. |
| `Sec_Appendix_A.ipynb` | Outputs Table A-1 (story-level stats) and Table A-2 (Cronbach's alpha and Spearman correlation). |
| `Sec_Appendix_C.ipynb` | Outputs Table C.1 (eigenvalues), Table C.2 (factor loadings), and a 3D PCA plot (Figure C-1). |
| `Sec_Appendix_D1.ipynb` | Outputs Table D-1 and Figure D-1 for KMeans cluster evaluation. |
| `Sec_Appendix_D2.ipynb` | Outputs Table D-2 and Figure D-2 for hierarchical clustering and dendrograms. |
| `Sec_Appendix_D3.ipynb` | Outputs Table D-3 with pairwise t-tests and rank correlation results by model. |
| `Sec_Appendix_E1.ipynb` | Outputs Table E-1: top 10 TF-IDF keywords per model from evaluation comments. |
| `Sec_Appendix_E2.ipynb` | Outputs Table E-2: top 10 TF-IDF keywords per session cluster (based on PCA + KMeans). |

## Data

The analysis uses a single CSV file:

**`official_row_data.csv`**

| Column       | Description                                      |
|--------------|--------------------------------------------------|
| `story`      | Story title                                      |
| `model`      | Language model used (e.g. ChatGPT4.5, Gemini-2.5)|
| `session`    | Evaluation session number (1–7)                  |
| `score`      | Numerical score (0–100 scale)                    |
| `comment`    | Textual commentary on the story by the model     |

> Note: In some analyses (e.g., Table E-2), sessions Notebook LM-2 through -7 are excluded.

## Environment

Tested with:

- Python 3.11.5 (Anaconda)
- pandas 2.0.3  
- numpy 1.25.2  
- matplotlib 3.10.0  
- seaborn 0.13.2  
- scikit-learn 1.6.1  
- scipy 1.15.2  

Install all dependencies with:

```bash
pip install -r requirements.txt
```

## Execution

You can execute each notebook in order using Jupyter Notebook or Jupyter Lab. Suggested order:

1. `Sec_4.1_Z-score.ipynb`  
2. `Sec_4.2_Boxplot.ipynb`  
3. `Sec_4.5_PCA.ipynb`  
4. `Sec_4.6_k-means.ipynb`  
5. `Sec_Appendix_A.ipynb`  
6. `Sec_Appendix_C.ipynb`  
7. `Sec_Appendix_D1.ipynb`  
8. `Sec_Appendix_D2.ipynb`  
9. `Sec_Appendix_D3.ipynb`  
10. `Sec_Appendix_E1.ipynb`  
11. `Sec_Appendix_E2.ipynb`  

## Notes

- PCA dimensionality is limited to PC1–PC4.
- Comments are analyzed with TF-IDF after custom preprocessing and stopword filtering.
- Clustering is applied to PCA loadings of model-session score vectors.

## License

This project is open-sourced under the MIT License.
