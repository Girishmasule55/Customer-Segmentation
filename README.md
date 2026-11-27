# Credit Card Customer Segmentation

unsupervised-learning project that segments credit-card customers using K-Means, Agglomerative Hierarchical Clustering and DBSCAN.

## Business problem

A bank wants to move away from one-size-fits-all card upgrades, reward programmes and credit-limit reviews. This project explores customer behaviour and creates groups that can help the bank plan more relevant engagement.

## Dataset

Download **Credit Card Dataset for Clustering** from Kaggle:

https://www.kaggle.com/datasets/arjunbhasin2013/ccdata

After downloading, place `CC_GENERAL.csv` inside the `data/` folder. The dataset is not included in this repository.

## Project structure

```text
creditcard-segmentation-unsupervised-learning/
├── data/
│   └── README.md
├── models/
│   └── (generated after running the notebook)
├── notebooks/
│   └── CreditCardSegmentation_UnsupervisedLearning.ipynb
├── reports/
│   └── summary_report.md
├── .gitignore
├── README.md
└── requirements.txt
```

## Setup

1. Clone or download this repository.
2. Create and activate a virtual environment (recommended).
3. Install dependencies:

   ```bash
   pip install -r requirements.txt
   ```

4. Download `CC_GENERAL.csv` from the Kaggle link above and put it in `data/`.
5. Start Jupyter:

   ```bash
   jupyter notebook
   ```

6. Open `notebooks/CreditCardSegmentation_UnsupervisedLearning.ipynb` and run all cells from top to bottom.

## Methods included

- **K-Means:** Elbow method, silhouette score, cluster plots and customer profiles.
- **Agglomerative Clustering:** Ward dendrogram and comparison of Ward, complete and average linkage.
- **DBSCAN:** k-nearest-neighbour distance curve, parameter grid, noise-point analysis and cluster profiles.

The notebook also covers EDA, median imputation, IQR-based upper capping, log transformation, StandardScaler and internal clustering metrics.

## Cluster personas

The notebook provides profile tables. Use the actual averages from your run before assigning final persona names. Possible interpretations include:

- **Premium Revolvers:** higher balances and credit limits; may be suitable for balance-transfer or EMI conversations.
- **Frequent Transactors:** regular purchase and payment activity; may respond to relevant rewards.
- **Cash-Advance Reliant:** comparatively high cash-advance usage; may need a careful affordability or product-fit review.
- **Low-Activity / Dormant:** limited purchase activity; may respond to a suitable reactivation campaign.
- **New-to-Card:** shorter tenure, if supported by the profile.

These are examples, not precomputed findings. Cluster numbers and actual personas depend on the dataset and model run.

## Saved model files

Running the notebook creates:

- `models/cc_scaler.pkl`
- `models/cc_segmentation_model.pkl`
- `models/feature_columns.pkl`

K-Means is saved as the final model because it supports prediction for new rows. The notebook's `predict_segment()` returns a cluster label and a simple suggested persona name; review the profile-based persona rules before presenting them as final business conclusions. Agglomerative clustering and standard DBSCAN do not have a direct `predict()` method for unseen customers.



## Notes

- The notebook has not been pre-run because the Kaggle CSV was not supplied with the project brief.
- Run it locally to generate real plots, metrics, cluster profiles and model files.
- Do not commit the dataset or any private customer data unless you have permission.
