# Summary Report — Credit Card Customer Segmentation

## Business problem and dataset

The project explores how a bank can move away from offering the same card upgrades, rewards and credit-limit decisions to every cardholder. The aim is to discover groups of customers with similar usage patterns and translate those groups into practical actions for the Cards and Payments team. The analysis uses the anonymised Credit Card Dataset for Clustering from Kaggle, which contains monthly behavioural and financial information such as balance, purchases, cash advances, payments, credit limit and tenure.

## Feature engineering and preprocessing

The `CUST_ID` column is removed because it identifies a customer rather than describing behaviour. Missing values in `CREDIT_LIMIT` and `MINIMUM_PAYMENTS` are filled with their median values. Duplicate rows are checked and removed. Additional features are created to describe monthly average purchases, monthly average cash advances, balance relative to credit limit, and payments relative to minimum payments. Division-by-zero cases are handled so the calculations remain valid.

Extreme upper values in selected monetary columns are capped using the upper IQR rule (Q3 + 3 × IQR), rather than deleting customers. Monetary features are transformed using `log1p` to reduce right-skew. StandardScaler is then applied because distance-based clustering algorithms are sensitive to differences in feature scale. The notebook includes plots and summary tables so these preprocessing choices can be reviewed.

## Clustering methods and evaluation

Three methods are compared. K-Means is tested across multiple values of k using inertia and silhouette score. Agglomerative clustering is explored with a Ward dendrogram and compared using Ward, complete and average linkage. DBSCAN is tuned with a k-nearest-neighbour distance curve and a small grid of epsilon and minimum-sample values. The models are evaluated using Silhouette Score, Davies-Bouldin Index and Calinski-Harabasz Index. DBSCAN evaluation excludes noise points and reports the percentage of customers marked as noise.

**Result to complete after running the notebook:** The best-performing algorithm by the internal metrics was **[enter algorithm]**. Its final parameters were **[enter parameters]**. This result **[did / did not]** match the business expectation because **[explain using the cluster profiles]**.

## Customer segments and actions

Use the generated cluster profile tables to complete this section with the real results:

- **Cluster [number] — [persona]:** [Describe the balance, purchase, cash-advance, payment and tenure pattern]. Suggested action: [one suitable bank action].
- **Cluster [number] — [persona]:** [Describe the pattern]. Suggested action: [one suitable bank action].
- **Cluster [number] — [persona]:** [Describe the pattern]. Suggested action: [one suitable bank action].

Do not assign a persona based only on a cluster number. Cluster labels are arbitrary; the feature averages should support the interpretation.

## Next steps

A future version could include repayment history, delinquency indicators, product ownership, rewards redemption, customer engagement and channel preferences, subject to appropriate consent, privacy and governance controls. The bank could also test whether the segments remain stable over time, review them with relationship managers, and build a scoring service for assigning new customers to the K-Means segments. Business impact should be measured through controlled campaigns rather than assumed from clustering scores alone.
