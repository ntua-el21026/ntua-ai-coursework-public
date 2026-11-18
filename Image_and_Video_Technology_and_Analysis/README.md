# Image and Video Technology and Analysis Lab Projects

**Course:** Image and Video Technology and Analysis (NTUA, Spring 2026)
**Student:** Michail Athanasios Peppas

---

## Overview

This directory contains two lab exercises covering both classical image representation methods and modern CNN-based image classification:

1. **Lab 1:** Laplacian pyramid image coding, exact reconstruction, entropy analysis, and quantization experiments on RGB and grayscale images.
2. **Lab 2:** CNN image classification on a 20-class CIFAR-100 subset, comparing LeNet, AlexNet, VGG, a custom MyCNN model, regularization strategies, and transfer learning with VGG19 and EfficientNetB0.

The coursework folder preserves two notebooks and their recorded observations. The original exercise statements, Lab 2 template, teaching notebooks, and four paper copies are accessed through the links below. They served as instructional scaffolding and reading context. The student implementations and evaluations remain in the notebooks.

The notebooks use NumPy, pandas, Matplotlib, Pillow, scikit-image, TensorFlow/Keras, and scikit-learn in notebook environments. Exact historical versions and compatibility with current Colab/local runtimes are not frozen; inspect each notebook before preparing a new environment.

---

## Repository Structure

```bash
Image_and_Video_Technology_and_Analysis/
├── lab1/
│   ├── IVTA_03121026_Peppas_Michael_1.ipynb
│   │                                   # Main notebook: Laplacian pyramid theory, implementation, and experiments
├── lab2/
│   ├── IVTA_03121026_Peppas_Michael_2.ipynb
│   │                                   # Main notebook: CNN comparison, regularization, and transfer learning
│   ├── CNN_Lab_Full_Theory.md         # Theory and oral-exam notes
│   └── implementations/               # Source-link files for LeNet, AlexNet, and VGG references
├── lab_material/
│   ├── README.md                      # Course references and attribution
│   └── lab2/                          # Verified TensorFlow excerpts
└── README.md                          # Project overview and instructions
```

---

## Lab 1 - Laplacian Pyramid Image Coding

**Path:** `lab1/`
**Notebook:** `IVTA_03121026_Peppas_Michael_1.ipynb`
**Reading:** [Official sources and papers](#reference-material)

### Description

This lab studies the **Laplacian Pyramid** as both a multiscale image representation and a compact image coding method. The notebook first explains the theory behind Gaussian/Laplacian pyramids and entropy, then implements the full pipeline from scratch, and finally evaluates how kernel shape, pyramid depth, and quantization strength affect reconstruction quality and coding efficiency.

### Key Concepts & Techniques

- **Gaussian and Laplacian Pyramids**
  - Recursive `REDUCE` and `EXPAND` operators.
  - Multiscale decomposition into residual bands and a final coarse Gaussian level.
- **Separable Filtering**
  - Construction of the 5-tap generating kernel parameterized by `a`.
  - Efficient 2D convolution using horizontal and vertical 1D passes.
- **Exact Reconstruction**
  - Expand-and-sum decoding from the coarsest level back to full resolution.
  - Handling of odd image sizes and boundary conditions with reflect padding.
- **Uniform Quantization**
  - Level-wise quantization of Laplacian coefficients.
  - Study of the rate-distortion tradeoff as bin size increases.
- **Entropy-Based Coding Analysis**
  - Shannon entropy estimation per pyramid level.
  - Estimated coding rate in bits per original sample for the full pyramid.
- **Experimental Evaluation**
  - Test images: **Lena (RGB)** and `skimage.data.camera()` (grayscale).
  - Parameter sweeps over:
    - `a in {0.3, 0.4, 0.5, 0.6, 0.7}`
    - `depth in {3, 4, 5, 6}`
    - `bin_size in {4, 16}`

### Implementation Details

- **Languages & Libraries:** Python, NumPy, pandas, Matplotlib, Pillow, scikit-image.
- **Core Functions:**
  - `GKernel(a)`
  - `_separable_conv2d(I, h)`
  - `GREDUCE(I, h)`
  - `GPyramid(I, a, depth)`
  - `GEXPAND(I, h, out_shape=None)`
  - `LPyramid(I, a, depth)`
  - `L_Pyramid_Decode(L, a)`
  - `L_Quantization(L, bin_size)`
  - `reconstruction_error(original, reconstructed)`
- **Metrics:**
  - Max absolute reconstruction error
  - Mean Squared Error (MSE)
  - PSNR
  - Entropy per level
  - Estimated bits per original sample

### Recorded results

- **Reconstruction before quantization**
  - Reconstruction is effectively exact for both images across all tested `a` and `depth` values, with MSE on the order of `10^-31` to `10^-30`.
- **Best global kernel parameter**
  - The lowest estimated coding rate is achieved near **`a = 0.6`**, in agreement with the reference paper.
  - Best combinations found in the notebook:
    - **Lena (RGB):** `a = 0.6`, `depth = 5`, `total_bpp = 5.769710`
    - **camera (grayscale):** `a = 0.6`, `depth = 6`, `total_bpp = 5.484721`
- **Per-level entropy behavior**
  - The finest residual level `L0` is optimized at **`a = 0.6`** for both images.
  - Intermediate levels are mostly optimized near **`a = 0.5`**, showing that entropy-optimal behavior depends on scale.
- **Quantization tradeoff**
  - **Lena (RGB):**
    - `bin_size = 4`: `5.770946 -> 3.178666 bpp`, `PSNR = 39.45 dB`
    - `bin_size = 16`: `5.770946 -> 0.937192 bpp`, `PSNR = 28.77 dB`
  - **camera (grayscale):**
    - `bin_size = 4`: `5.484721 -> 3.122948 bpp`, `PSNR = 40.47 dB`
    - `bin_size = 16`: `5.484721 -> 1.303582 bpp`, `PSNR = 29.27 dB`

---

## Lab 2 - CNN Image Classification and Transfer Learning

**Path:** `lab2/`
**Notebook:** `IVTA_03121026_Peppas_Michael_2.ipynb`
**Supporting files:** [CNN theory notes](lab2/CNN_Lab_Full_Theory.md), [external implementation references](lab2/implementations/) and [official readings](#reference-material). The reference directory contains link records for LeNet, AlexNet and VGG.

### Description

This lab studies the theory and practice of **Convolutional Neural Networks (CNNs)** for image classification. It first compares the historical design ideas behind LeNet, AlexNet, and VGG, then applies those ideas to a student-specific 20-class CIFAR-100 subset. The implementation evaluates CNNs trained from scratch, regularized versions of a custom model, and ImageNet-pretrained transfer-learning models.

### Key Concepts & Techniques

- **CNN Theory and Architecture Comparison**
  - Local receptive fields, weight sharing, feature maps, and pooling.
  - LeNet, AlexNet, and VGG design principles.
  - Comparative analysis of layers, filter sizes, activations, parameter counts, pooling, dropout, and performance behavior.
- **Dataset Preparation**
  - CIFAR-100 fine-label dataset.
  - Student-specific class subset selected with `team_seed = 26`.
  - Label remapping from original CIFAR-100 IDs to contiguous labels `0..19`.
- **Training from Scratch**
  - Adapted `LeNet`, compact `AlexNet`, compact `VGG`, and custom `MyCNN`.
  - Common hyperparameter search over optimizer, loss, and batch size.
  - Final training and evaluation with accuracy, macro-F1, and weighted-F1.
- **Overfitting Control**
  - Dropout variants for `MyCNN`.
  - Light and medium data augmentation.
  - Train-validation gap analysis.
- **Transfer Learning**
  - ImageNet-pretrained `VGG19` and `EfficientNetB0`.
  - Frozen-base training followed by careful fine-tuning.
  - Model-specific preprocessing and resizing to `128 x 128 x 3`.

### Implementation Details

- **Languages & Libraries:** Python, TensorFlow/Keras, NumPy, pandas, Matplotlib, scikit-learn, requests, and tqdm.
- **Dataset Subset:** 20 CIFAR-100 classes selected by `team_seed = 26`, including bus, chimpanzee, cloud, dinosaur, forest, fox, girl, hamster, lobster, motorcycle, oak_tree, pine_tree, seal, shrew, skunk, snake, sweet_pepper, telephone, tiger, and worm.
- **Core Components:**
  - `build_lenet`
  - `build_alexnet`
  - `build_vgg`
  - `build_mycnn`
  - `MacroF1Callback`
  - `build_q2_mycnn`
  - `build_q3_transfer_model`
  - `set_q3_frozen_base`
  - `set_q3_finetuning`
- **Training Setup:**
  - Best common setup from grid search: Adam optimizer, KL divergence loss, batch size 32, final training for 50 epochs.
  - Question 2 grid over dropout and augmentation variants.
  - Question 3 frozen-base training followed by fine-tuning of top pretrained layers.

### Recorded results

The model-comparison procedure uses test macro-F1 for selection, so these comparisons are exploratory.

- **Question 1 - CNNs trained from scratch**
  - `MyCNN` gives the best scratch-trained result:
    - Test accuracy: `0.6205`
    - Test macro-F1: `0.6309`
  - Ranking by test macro-F1: `MyCNN > VGG > AlexNet > LeNet`.
- **Question 2 - MyCNN regularization**
  - Best regularized model: `MyCNN_Best_Dropout_Augmentation`.
    - Dropout: `0.3`
    - Augmentation: `medium`
    - Test accuracy: `0.6595`
    - Test macro-F1: `0.6607`
    - Overfitting gap: `0.1082`
  - Data augmentation is more effective than dropout alone in this experiment.
- **Question 3 - Transfer learning**
  - Best overall model: fine-tuned `EfficientNetB0`.
    - Trainable parameters: `1,816,436`
    - Test accuracy: `0.8710`
    - Test macro-F1: `0.8702`
    - Test weighted-F1: `0.8702`
  - In the recorded comparison, this model had higher test macro-F1 than the evaluated models trained from scratch.

---

## Reference Material

Read the instructor handouts and teaching notebooks through the [official course sources](lab_material/README.md). The local TensorFlow excerpts retain only the verified code and its license.

- Burt and Adelson, *The Laplacian Pyramid as a Compact Image Code*. [IEEE DOI](https://doi.org/10.1109/TCOM.1983.1095851)
- LeCun et al., *Handwritten Digit Recognition with a Back-Propagation Network*. [NeurIPS proceedings](https://proceedings.neurips.cc/paper_files/paper/1989/file/53c3bce66e43be4f209556518c2fcb54-Paper.pdf)
- Krizhevsky et al., *ImageNet Classification with Deep Convolutional Neural Networks*. [NeurIPS proceedings](https://proceedings.neurips.cc/paper/2012/hash/c399862d3b9d6b76c8436e924a68c45b-Abstract.html)
- Simonyan and Zisserman, *Very Deep Convolutional Networks for Large-Scale Image Recognition*. [arXiv author manuscript](https://arxiv.org/abs/1409.1556v6)

---

## Prerequisites

Use an isolated Python environment supported by the TensorFlow version you select for Lab 2. The submissions do not pin the original dependency versions. A local Jupyter environment needs the following packages.

```bash
python -m pip install jupyterlab numpy pandas matplotlib pillow scikit-image scikit-learn tensorflow requests tqdm
```

---

## Usage

1. **Open this directory in a local checkout or clone the repository.**

   ```bash
   git clone https://github.com/ntua-el21026/ntua-ai-coursework-public.git
   cd ntua-ai-coursework-public/Image_and_Video_Technology_and_Analysis
   ```

2. **Install dependencies** listed above.
3. **Open the lab notebooks** with Jupyter or Google Colab:
   - `lab1/IVTA_03121026_Peppas_Michael_1.ipynb`
   - `lab2/IVTA_03121026_Peppas_Michael_2.ipynb`
4. **Run cells sequentially** in a copy with authorized inputs and review the original external download cells first.
5. **Lab 1 image input:** use a separately authorized local image. If you use a substitute, label its outputs as a new run. Review or skip the historic image download cells.

---

## Inputs, paths, and evidence

The submitted notebooks are [Lab 1](lab1/IVTA_03121026_Peppas_Michael_1.ipynb) and [Lab 2](lab2/IVTA_03121026_Peppas_Michael_2.ipynb). See the [course-reference guide](lab_material/README.md) for original course access and the verified TensorFlow excerpts.

Lab 1 uses the [scikit-image camera sample](https://scikit-image.org/docs/stable/api/skimage.data.html#skimage.data.camera), credited to Lav Varshney under CC0, and its recorded run also used Lena. Four identifiable Lena panels are omitted from the included notebook outputs. Numeric results and the independent camera panels remain. Source cells retain the historical input procedure, so use a cleared local input before rerunning. The four edited output pairs use zero-based coordinates (8, 1), (10, 0), (12, 0), and (18, 1). Lab 2 downloads CIFAR-100 and pretrained Keras weights and reads the course's class-selection/label tables from Pastebin. `q1_grid_results.csv` is a generated intermediate needed by the resume section; it is not committed, so a fresh runtime needs the original exported CSV or a new Q1 grid run. The included notebook preserves the submission-specific split and recorded metrics. Lab 2 cells 4, 9, 13, 21, 31 and 40 use revised preparation code or summarized instructor directions. Other cells and recorded results retain their historical contents. Lab 2 writes further CSV/plot outputs to its configured paths.

The result summaries above describe the stored coursework outputs. Lab 2 selects model configurations using test macro-F1, so the selected comparisons are exploratory and are not untouched-holdout estimates. Exact historical dependencies and independent numerical replay have not been re-established. Use a separate working copy and output directory for new runs; see the [asset inventory](../docs/ASSETS.md).
