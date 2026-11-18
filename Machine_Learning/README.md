# Machine Learning

Two individual NTUA coursework notebooks by **Michail Athanasios Peppas**. Both retain Greek assignment text, implementations, and recorded outputs.

## Labs and supplied inputs

| Lab | Work implemented | Input basenames |
| --- | --- | --- |
| [Lab 1](ML_Lab1/ML_Lab1.ipynb) | RainTomorrow classification; missing-value handling, preprocessing, classifier comparisons, grid search, and test predictions | External `train-val.csv` and `test.csv` in the Lab 1 notebook working directory |
| [Lab 2](ML_Lab2/ML_Lab2.ipynb) | Salinas hyperspectral clustering with KMeans, PCA, and fuzzy C-means; EuroSAT image clustering/feature experiments with MobileNetV3Small | External `salinas_image.npy` and `salinas_labels.npy` in the Lab 2 notebook working directory |

Lab 1 compares scikit-learn classifiers including logistic regression, Gaussian naive Bayes, K-nearest neighbors, decision trees, random forests, SVMs, and MLPs. Lab 2 evaluates cluster assignments using adjusted Rand scores and silhouette measures where applicable. The notebooks record the comparison settings and results.

## Running a copy

From a local checkout, enter `Machine_Learning/`. To work from a clone, use the following commands.

```bash
git clone https://github.com/ntua-el21026/ntua-ai-coursework-public.git
cd ntua-ai-coursework-public/Machine_Learning
```

Use a separate environment for the chosen notebook. Common libraries include NumPy, pandas, Matplotlib, seaborn, and scikit-learn. Lab 2 imports `FCM` from the **`fuzzy-c-means`** package and TensorFlow/Keras for the image-feature section; `scikit-fuzzy` is not the imported FCM dependency.

The notebooks load these basenames from the kernel working directory. The empty historical `ML_Lab1_utils` and `ML_Lab2_utils` directories are not needed for setup. Stage the authorized files directly next to the corresponding notebook in a separate working copy or explicitly configure the working directory. Use the exact input basenames and [check the recorded input identities](../docs/ASSETS.md#authorized-local-inputs) before asserting reproduction. Inspect cells before execution: Lab 2 downloads/extracts EuroSAT into `2750/` and obtains pretrained weights; those large third-party assets are not versioned here. Historical download cells disable certificate checks; obtain and verify the dataset through an authorized trusted source when preparing a new run.

Lab 1 writes `submission_nopt_fin.csv` and `submission_opt_fin.csv` to the working directory. Keep new predictions and outputs separate from the original evidence. Exact package versions and a complete historical environment lock are not available.

## Evidence

The original assignment headers identify different course editions. The Lab 1 brief is labelled 2024–25 and the Lab 2 brief 2023–24. The headers document the assignment editions. The submission dates are unverified. Both briefs include a course notice prohibiting online publication of lab solutions.

See the [asset inventory](../docs/ASSETS.md) for external datasets.
