# Artificial Intelligence

Two NTUA laboratory submissions by **Michail Athanasios Peppas**. The notebooks contain implementation, analysis, and historical outputs; the original course instructions and AI-use disclosures remain part of the submissions.

## Lab 1: maze search and adversarial agents

Open [AI_Lab1.ipynb](AI_Lab1/AI_Lab1.ipynb). It implements a randomized DFS-style maze generator, a parameterized priority-queue pathfinder, Manhattan/Euclidean/Chebyshev/Octile heuristics, search visualizations, and Alpha-Beta ghost-avoidance experiments. A bonus section uses five manually drawn mazes and a hill-climbing agent.

The implementation is inside the notebook. [AI_Lab1_utils/](AI_Lab1/AI_Lab1_utils/) contains five PNG images, rather than separate Python helper modules. The notebook was independently retrieved from the original Colab link and integrated with limited local asset-path corrections. See the [Lab 1 guide](AI_Lab1/README.md) for local/Colab use and [provenance.json](AI_Lab1/provenance.json) for hashes and the exact change scope.

Stored labels and conclusions are historical coursework evidence. The zero-cost/zero-heuristic variant labeled BFS uses priority-queue tie ordering rather than a FIFO queue. No new optimality, timing, or win-rate result is claimed here.

## Lab 2: hybrid movie recommendation

Open [AI_Lab2.ipynb](AI_Lab2/AI_Lab2.ipynb). Python reads movie metadata, asserts facts into SWI-Prolog through `pyswip`, and combines symbolic movie similarities with user ratings. The notebook includes tiered similarity schemes, caching, parameter comparisons, and precision/recall/F1 evaluation.

[AI_Lab2_utils/](AI_Lab2/AI_Lab2_utils/) includes `db.pl` and the recorded `train_ratings.csv` and `test_ratings.csv`. Supply authorized `movies_metadata.csv` for an exact rerun or use the separate [fictional demo fixture](AI_Lab2/AI_Lab2_utils/synthetic_demo/README.md) for an illustrative run. Recommendation logic is in notebook cells; there is no separate `recommender.py` module.

Requirements include Python, NumPy, pandas, Matplotlib, scikit-learn, tqdm, `pyswip`, and an installed SWI-Prolog runtime. The notebook contains Colab installation and Drive cells, and repeats the original personal Drive path in several places. For a local run, copy `db.pl`, `train_ratings.csv` and `test_ratings.csv` from `AI_Lab2_utils/` into a separate working directory with an authorized `movies_metadata.csv`. Skip the Drive-mount cell and update the repeated `path` assignments in a notebook copy. Use a trailing separator because the notebook concatenates paths with file basenames. For the demo, follow its separate staging instructions. For Colab, provide the same authorized inputs in the runtime and use their corresponding runtime path. Preserve the submitted notebook when adapting paths for a rerun.

## Reproducibility

The labs use different dependencies and are not distributed as an installable package or a locked environment. Inspect setup cells before execution and record actual versions, seeds, and input hashes. Run experiments on a copy and retain the original outputs.
