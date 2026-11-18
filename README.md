# NTUA AI Coursework — eight laboratory submissions

This portfolio presents eight NTUA Electrical and Computer Engineering laboratory submissions by **Michail Athanasios Peppas**. The work spans heuristic search, symbolic recommendation, statistical learning, neural network evaluation, and image analysis. Each notebook preserves the implemented methods, recorded observations, and submission context.

## Implemented work and evidence

| Course | Lab | Contribution and evidence |
| --- | --- | --- |
| [Artificial Intelligence](Artificial_Intelligence/README.md) | 1 | [Maze generation, priority-queue search variants, and adversarial Alpha–Beta agents](Artificial_Intelligence/AI_Lab1/AI_Lab1.ipynb). Five original hand-drawn mazes and their [provenance](Artificial_Intelligence/AI_Lab1/README.md) remain available. |
| Artificial Intelligence | 2 | [Python/SWI-Prolog movie recommendation](Artificial_Intelligence/AI_Lab2/AI_Lab2.ipynb). Retained Prolog rules and numeric ratings support the recorded analysis. A separate [synthetic fixture](Artificial_Intelligence/AI_Lab2/AI_Lab2_utils/synthetic_demo/README.md) demonstrates the input interface. |
| [Machine Learning](Machine_Learning/README.md) | 1 | [RainTomorrow classification](Machine_Learning/ML_Lab1/ML_Lab1.ipynb) with preprocessing, classifier comparison, and model selection. |
| Machine Learning | 2 | [Salinas hyperspectral clustering and EuroSAT feature experiments](Machine_Learning/ML_Lab2/ML_Lab2.ipynb) with spatial/spectral analysis and pretrained image features. |
| [Neural Networks and Deep Learning](Neural_Networks_and_Deep_Learning/README.md) | 1 | [WideResNet configurations, Mixup, calibration, and CIFAR-10-C evaluation](Neural_Networks_and_Deep_Learning/DL_Lab1/DL_Lab1.ipynb). |
| Neural Networks and Deep Learning | 2 | [Transformer workflows](Neural_Networks_and_Deep_Learning/DL_Lab2/DL_Lab2.ipynb) for Yelp Polarity, PiQA, TruthfulQA, and Winogrande. |
| [Image and Video Technology and Analysis](Image_and_Video_Technology_and_Analysis/README.md) | 1 | [Gaussian and Laplacian pyramids](Image_and_Video_Technology_and_Analysis/lab1/IVTA_03121026_Peppas_Michael_1.ipynb) with reconstruction, entropy, and quantization experiments. |
| Image and Video Technology and Analysis | 2 | [CIFAR-100 subset classification](Image_and_Video_Technology_and_Analysis/lab2/IVTA_03121026_Peppas_Michael_2.ipynb) with CNN comparison, regularization, and transfer learning. |

## Validation and interpretation

The saved outputs document the original coursework runs. Some outputs lack execution counts, and the original environments are only partly pinned. The IVTA classifier comparisons are exploratory because model selection used test macro-F1. The AI Lab 1 variant labelled BFS uses zero edge costs and breaks ties by coordinate, so its traversal can differ from FIFO breadth-first search.

Local checks parsed all ten notebook containers, verified the five maze images against their recorded hashes, and checked the synthetic movie fixture’s schema and joins. Those checks cover notebook structure and input compatibility. The numerical experiments and Prolog code were not rerun. The [asset inventory](docs/ASSETS.md) identifies the missing inputs and their provenance, including the original movie metadata, weather split, Salinas arrays, course helpers, model weights, and public benchmark dependencies. The 12-title fixture exercises the recommendation interface. Reproducing the historical results requires the original movie metadata.

## Inspection and setup

Open the notebooks to review the experiments and saved outputs. Clone the repository for a working copy.

```bash
git clone https://github.com/ntua-el21026/ntua-ai-coursework-public.git
cd ntua-ai-coursework-public
```

Follow the relevant course guide and stage authorized inputs in a separate working copy. Runtime requirements vary across the eight submissions. The GPU workflows use a compatible managed runtime. Keep new runs, model/data versions, seeds, and package records separate from the original submissions.

The [course and reading references](docs/lecture_slides/README.md) and [IVTA teaching excerpts](Image_and_Video_Technology_and_Analysis/lab_material/README.md) document the boundary between instructor material and student work. The [MIT notice](LICENSE) applies to original work. Third-party files use their own licenses and attribution.
