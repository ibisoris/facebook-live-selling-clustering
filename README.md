# Facebook Live Selling Engagement Clustering

This project uses unsupervised machine learning to group Facebook Live Selling posts based on audience engagement. Instead of predicting a known label, the notebook looks for natural patterns in the data, such as posts with low engagement, high comment/share activity, or high reaction activity.

The main work is contained in `facebook_live_selling_clustering.ipynb`.

## Project Highlights

- Uses Facebook Live Selling engagement data.
- Explores post engagement features such as reactions, comments, shares, likes, loves, wows, hahas, sads, and angrys.
- Cleans the dataset by removing empty columns.
- Scales the engagement features before clustering.
- Uses the elbow method and silhouette analysis to help choose the number of clusters.
- Compares K-Means clustering with Agglomerative Clustering.
- Uses PCA to visualise clusters in two dimensions.
- Profiles each cluster to explain what the groups mean in plain language.

## Why This Matters

Facebook Live Selling depends heavily on audience interaction. Understanding engagement patterns can help sellers, marketers, and analysts identify different types of posts, such as normal engagement posts, highly interactive posts, or posts that receive many reactions but fewer comments and shares.

This type of analysis can support better content planning, campaign review, and audience behaviour understanding.

## Problem Statement

The goal of this project is to answer the question:

> Can Facebook Live Selling posts be grouped into meaningful engagement categories using clustering techniques?

This is an unsupervised learning problem. That means the dataset does not provide a target label for the model to predict. Instead, the algorithm discovers groups based on similarities in engagement behaviour.

## Project Files

| File | Purpose |
| --- | --- |
| `facebook_live_selling_clustering.ipynb` | Main Jupyter Notebook containing the full clustering analysis. |
| `Live_20210128.csv` | Dataset containing Facebook Live Selling post engagement data. |
| `requirements.txt` | Python packages needed to run the notebook. |
| `.gitignore` | Tells Git which temporary or local files should not be uploaded. |

## Dataset Overview

The dataset contains 7,050 Facebook posts and 16 columns. The main engagement columns used for clustering include:

- `num_reactions`
- `num_comments`
- `num_shares`
- `num_likes`
- `num_loves`
- `num_wows`
- `num_hahas`
- `num_sads`
- `num_angrys`

The original dataset also includes metadata columns such as `status_id`, `status_type`, and `status_published`. Empty columns named `Column1`, `Column2`, `Column3`, and `Column4` are removed during cleaning.

## What The Notebook Does

The notebook follows these main steps:

1. Loads the dataset from `Live_20210128.csv`.
2. Reviews the dataset structure, columns, missing values, and summary statistics.
3. Removes empty columns that do not add useful information.
4. Explores engagement patterns using histograms, boxplots, count plots, pair plots, and a correlation heatmap.
5. Selects numeric engagement features for clustering.
6. Scales the selected features so that large-value columns do not dominate the clustering.
7. Uses the elbow method to inspect possible values of `k`.
8. Uses silhouette scores to compare possible cluster counts.
9. Trains a K-Means model with 3 clusters.
10. Creates a hierarchical clustering dendrogram.
11. Trains an Agglomerative Clustering model with 3 clusters.
12. Compares models using Silhouette Score and Davies-Bouldin Index.
13. Builds cluster profiles to explain each engagement group.
14. Compares clusters with post type using a stacked bar chart.

## Methodology

| Stage | What Happens |
| --- | --- |
| Data loading | The CSV file is loaded into a pandas DataFrame. |
| Data cleaning | Empty columns are removed from the dataset. |
| Exploratory analysis | Charts and summary statistics are used to understand engagement patterns. |
| Feature selection | Numeric engagement metrics are selected for clustering. |
| Scaling | StandardScaler is used so all selected features have comparable scale. |
| Cluster selection | Elbow and silhouette analysis are used to support the choice of 3 clusters. |
| Clustering | K-Means and Agglomerative Clustering are applied. |
| Visualisation | PCA is used to display clusters in two dimensions. |
| Evaluation | Silhouette Score and Davies-Bouldin Index are used to compare cluster quality. |
| Interpretation | Average engagement metrics are calculated for each cluster. |

## Results Summary

Both clustering methods produced similar results. K-Means performed slightly better based on the recorded evaluation metrics.

| Model | Silhouette Score | Davies-Bouldin Index |
| --- | ---: | ---: |
| K-Means | 0.749992 | 1.103370 |
| Agglomerative Clustering | 0.748571 | 1.149761 |

For Silhouette Score, higher is better. For Davies-Bouldin Index, lower is better.

Based on these results, K-Means was selected as the main clustering approach.

## Cluster Profiles

The K-Means model identified 3 engagement groups:

| Cluster | Size | Plain-English Interpretation |
| --- | ---: | --- |
| Cluster 1 | 6,405 posts | Low to normal engagement posts. These posts have relatively low reactions, comments, and shares. |
| Cluster 2 | 273 posts | Highly interactive posts. These posts have very high comments, shares, and love reactions. |
| Cluster 3 | 372 posts | High reaction/like posts. These posts receive many reactions and likes, but fewer comments and shares than Cluster 2. |

This suggests that Facebook Live Selling posts can attract engagement in different ways. Some posts generate broad reaction activity, while others create deeper interaction through comments and shares.

## How To Interpret The Results

The clusters should not be viewed as fixed business rules. They are data-driven groups based on the engagement features available in this dataset.

The most useful insight is that high engagement is not always the same type of engagement:

- one group is dominated by comments and shares
- another group is dominated by likes and reactions
- the largest group contains posts with lower overall engagement

For sellers or analysts, this can help distinguish posts that are simply liked from posts that generate stronger audience interaction.

## How To Run This Project

You need Python installed on your computer. Python 3.10 or newer is recommended.

### 1. Download or clone the project

If using Git:

```bash
git clone https://github.com/ibisoris/facebook-live-selling-clustering.git
cd facebook-live-selling-clustering
```

If you downloaded the project as a ZIP file, unzip it and open the project folder.

### 2. Create a virtual environment

On Windows:

```bash
python -m venv .venv
.venv\Scripts\activate
```

On macOS or Linux:

```bash
python -m venv .venv
source .venv/bin/activate
```

### 3. Install the required packages

```bash
pip install -r requirements.txt
```

### 4. Start Jupyter Notebook

```bash
jupyter notebook
```

Then open:

```text
facebook_live_selling_clustering.ipynb
```

Run the notebook cells from top to bottom.

## Dataset Note

The notebook expects the dataset file to be in the same folder as the notebook:

```text
Live_20210128.csv
```

This project uses a public Facebook Live Sellers dataset. The dataset remains subject to the terms of its original source. It is included here for educational and reproducibility purposes.

If the dataset is moved, renamed, or not included in the GitHub repository, the notebook will need to be updated with the correct file path.

## Technologies Used

- Python
- Jupyter Notebook
- pandas
- NumPy
- Matplotlib
- Seaborn
- scikit-learn
- SciPy

## Important Terms In Plain English

**Clustering**: A machine learning method that groups similar records together without needing pre-labelled answers.

**Unsupervised learning**: A type of machine learning where the model finds patterns by itself instead of learning from known labels.

**Engagement metrics**: Numbers that describe how people interacted with a post, such as likes, comments, shares, and reactions.

**K-Means**: A clustering method that groups records around central points called centroids.

**Agglomerative Clustering**: A hierarchical clustering method that starts with individual records and gradually merges them into groups.

**PCA**: A method used to reduce many features into fewer dimensions so patterns can be visualised more easily.

**Silhouette Score**: A score that measures how well-separated the clusters are. Higher values are better.

**Davies-Bouldin Index**: A score that measures cluster separation and compactness. Lower values are better.

## Limitations

This project is a notebook-based clustering analysis, not a production recommendation system. The clusters depend on the selected features, scaling method, and chosen number of clusters.

Possible limitations include:

- The analysis uses engagement metrics only, not post text, images, video content, or seller information.
- Clustering does not prove why a post performed well; it only groups posts with similar engagement patterns.
- The selected number of clusters is supported by metrics and visual checks, but other values of `k` could be explored.
- The dataset may reflect a specific time period, market, or seller behaviour pattern.

## Future Work

Useful next improvements would be:

- Add the exact dataset source link.
- Add a license file if the project is intended for reuse.
- Compare additional clustering methods such as DBSCAN or Gaussian Mixture Models.
- Add deeper cluster interpretation by status type and publishing time.
- Include text or content features if available.
- Build a simple dashboard for exploring cluster profiles.
