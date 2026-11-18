# Coursework assets and portability

This inventory distinguishes supplied files from external runtime dependencies.

| Lab | Available in this repository | External or runtime requirement |
| --- | --- | --- |
| AI 1 | [Notebook and five maze PNGs](../Artificial_Intelligence/AI_Lab1/README.md), including embedded historical animations/plots | Colab JavaScript bridge only for the interactive drawing UI. Personal Drive is no longer required for archived maze inputs. |
| AI 2 | Notebook, `db.pl`, historical train/test ratings and a fictional demo | SWI-Prolog and `pyswip`. See [AI Lab 2](../Artificial_Intelligence/README.md#lab-2-hybrid-movie-recommendation) for authorized input or isolated demo setup. |
| ML 1 | Notebook and recorded experiments | Authorized `train-val.csv` and `test.csv` in the notebook working directory. |
| ML 2 | Notebook and recorded experiments | Authorized Salinas `.npy` arrays, EuroSAT archive/extracted `2750/` images and MobileNetV3Small weights remain external third-party assets. Input `.npy` basenames are read from the current directory. |
| DL 1 | Notebook and original Drive-folder link | `wideresnet.py` is an external course helper module. Linked CIFAR data, checkpoints, logs, and runs were not imported. CIFAR-10-C is available from its [dataset record](https://zenodo.org/records/2535967). |
| DL 2 | Notebook | Hugging Face datasets and pretrained models, network access, sufficient storage/memory, and the required access. |
| IVTA 1 | Notebook and independent figures | Use an authorized local image when rerunning. [scikit-image camera image](https://scikit-image.org/docs/stable/api/skimage.data.html#skimage.data.camera) is credited to Lav Varshney under CC0. |
| IVTA 2 | Notebook, theory notes and [official references](../Image_and_Video_Technology_and_Analysis/README.md#reference-material) | CIFAR-100 and pretrained weights; class-selection/label tables hosted on Pastebin; original `q1_grid_results.csv` for resuming Q2 without rerunning Q1. |

## AI Lab 1 integration

The original source was independently downloaded twice from the ID in `AI_Lab1.txt`. Both downloads matched in size and SHA-256. The five existing PNGs match the notebook's original drawing outputs exactly. Only three asset-access cells were changed; all other source and all recorded outputs/counts/metadata are preserved. The [provenance record](../Artificial_Intelligence/AI_Lab1/provenance.json) provides the original and repository hashes plus image fingerprints.

## Remaining external material

The [DL Lab 1 Drive folder](https://drive.google.com/drive/folders/1Er6mi5njuZraQb7r9DknXDmBPM4uGjCM?usp=sharing) was accessible on 13 November 2026. Its listing contains the helper module and folders for data, weights, and runs. The linked artifact collection was not downloaded in bulk. Exact checkpoint/data identity and access can only be established after obtaining and hashing those inputs.

## Authorized local inputs

These five original research input files are external. The table records their intended working-directory paths and audited SHA-256 values. The table gives logical staging paths. The movie notebook constructs paths from a configurable directory string. Place its catalog, rules and rating splits together as described in [the movie recommendation guide](../Artificial_Intelligence/README.md#lab-2-hybrid-movie-recommendation). Use an authorized local copy with the exact schema. A matching checksum identifies the file and does not establish redistribution permission. The existing quantitative results describe the original inputs. Familiar-looking source data or replacement observations may produce different results.

- Movie metadata (4,803 rows). The original notebook cites a [Kaggle listing](https://www.kaggle.com/georgefila/movies-metadata). Confirm the terms and original field transformations before relying on it for exact reproduction. The original catalog supplied title, tag, synopsis and other movie fields for the Python-to-Prolog fact loading. The retained rating splits remain separate from the catalog and the fictional data. An archived preview that repeated two original taglines was replaced by a provenance notice. The separate [fictional demo](../Artificial_Intelligence/AI_Lab2/AI_Lab2_utils/synthetic_demo/README.md) has 12 records and its own ratings.
- Weather data (7,262 train/validation rows and 2,421 test rows). The prepared splits supply supervised features and labels for RainTomorrow and features for the recorded test predictions. Exact replay requires the original row identities and split. The exact prepared split is linked to the authors' course run. [Bureau terms](https://www.bom.gov.au/copyright) and [Rattle weatherAUS documentation](https://cran.r-project.org/web/packages/rattle/refman/rattle.html#weatherAUS) describe the likely upstream sources. Verify the split, row identities and provenance before publishing the original data.
- Salinas arrays. The radiance cube supplies spectral features and the labels are used for cluster evaluation. Ground-truth preparation has separate provenance from the original observation. The expected shapes are `(512, 217, 204)` for radiance and `(512, 217)` for prepared labels. Confirm numeric values, axis order and exact reuse terms when sourcing or converting the [EHU corrected scene and ground truth](https://www.ehu.eus/ccwintco/index.php/Hyperspectral_Remote_Sensing_Scenes). [NASA's policy](https://science.data.nasa.gov/about/license) for covered data is separate from terms on prepared ground-truth labels.
- The scoped course and software attributions for the retained TensorFlow code appear in the [IVTA lab material guide](../Image_and_Video_Technology_and_Analysis/lab_material/README.md). The root MIT notice is for original coursework material.

| Notebook working directory / required basename | Bytes | Archived SHA-256 |
| --- | ---: | --- |
| `Artificial_Intelligence/AI_Lab2/movies_metadata.csv` | 4423337 | `6cd02bdae5caa0ab0f82a34017f2c6a8c03cd762fb6a758e50b8226b2d3e4d83` |
| `Machine_Learning/ML_Lab1/train-val.csv` | 799853 | `53f31130297c316f864646d4f0502928467784059f4da722e6d2e1ddb2346753` |
| `Machine_Learning/ML_Lab1/test.csv` | 261279 | `a127680bef75973c0e09d61ec7ef1e390b666549b849697496e0a8d1dfc7075c` |
| `Machine_Learning/ML_Lab2/salinas_image.npy` | 45330560 | `87ba8f080eb373abc10d9e1eb0daf462add4c6e39cb0696290b274e6c2f65805` |
| `Machine_Learning/ML_Lab2/salinas_labels.npy` | 111232 | `81c1accfc57c897f0ed3c8a2620aa5a22150458c2a029be6ca13df71f79b0e92` |

## Externalized reference material

The [lecture index](lecture_slides/README.md) identifies the 53 course PDF paths by subject group. The [IVTA course guide](../Image_and_Video_Technology_and_Analysis/README.md#reference-material) links the two exercise statements and template via NTUA, along with the four publisher/author readings. They supplied teaching context and reference algorithms. The authored notebooks and the verified [TensorFlow excerpts](../Image_and_Video_Technology_and_Analysis/lab_material/README.md) remain. Reference-material access is independent of the conditional input staging above.
