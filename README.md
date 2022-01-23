# Ensemble Augmented-Shot Y-shaped Learning: State-Of-The-Art Few-Shot Classification with Simple Ingredients.
This repository is the official implementation Ensemble Augmented-Shot Y-shaped Learning: State-Of-The-Art Few-Shot Classification with Simple Ingredients.

EASY proposes a simple methodology, that reaches or even beats state of the art performance on multiple standardized benchmarks of the field, while adding almost no hyperparameters or parameters to those used for training the initial deep learning models on the generic dataset.

## Downloads 
Please click the [Google Drive link](https://drive.google.com/drive/folders/1fMeapvuR6Rby0HDHd5L74BEXRyiOF942) for downloading the features, backbones and datasets.

## Testing scripts for EASY
Run scripts to evaluate the features on FSL tasks for Y and ASY. For EY and EASY use the corresponding features.

### Inductive setup using NCM
Test features on miniimagenet using Y

    $ python main.py --dataset miniimagenet --model resnet12 --test-features "features path" --preprocessing ME

Test features on miniimagenet using ASY

    $ python main.py --dataset miniimagenet --model resnet12 --test-features "features path" --preprocessing ME --sample-aug 30

### Transductive setup using Soft k-means
Test features on miniimagenet using Y

    $ python main.py --dataset miniimagenet --model resnet12 --test-features "features path" --preprocessing ME --transductive --transductive-softkmeans --transductive-temperature-softkmeans 100

Test features on miniimagenet using ASY

    $ python main.py --dataset miniimagenet --model resnet12 --test-features "features path" --preprocessing ME --sample-aug 30 --transductive --transductive-softkmeans --transductive-temperature-softkmeans 20

## Training scripts for ASY
Train a model on miniimagenet using manifold mixup, self-supervision and cosine scheduler

    $ python main.py --dataset-path "dataset path" --dataset miniimagenet --model resnet12 --epochs 0 --manifold-mixup 500 --rotations --cosine --gamma 0.9 --milestones 100 --batch-size 128 --preprocessing ME 

## Important Arguments
Some important arguments for our code.

**Training arguments**
- `dataset`: choices=['miniimagenet', 'cubfs','tieredimagenet', 'fc100', 'cifarfs']
- `model`: choices=['resnet12', 'resnet18', 'resnet20', 'wideresnet', 's2m2r']

**Few-shot Classification**
- `preprocessing`: preprocessing sequence for few shot given as a string, can contain R:relu P:sqrt E:sphering and M:centering

## Few-shot classification Results

Experimental results on few-shot learning datasets with ResNet-12 backbone. We report our average results with 10000 randomly sampled episodes for both 1-shot and 5-shot evaluations.

**MiniImageNet Dataset (indcutive)**

|  Methods  | 1-Shot 5-Way | 5-Shot 5-Way |   
|:--------:|:------------:|:------------:|
| SimpleShot |     62.85 ± 0.20    |     80.02 ± 0.14    |
| Baseline++  |    53.97 ± 0.79 | 75.90 ± 0.61|
| TADAM | 58.50 ± 0.30 | 76.70 ± 0.30|
|ProtoNet [10] | 60.37 ± 0.83 | 78.02 ± 0.57|
|R2-D2 (+ens) [20] | 64.79 ± 0.45 | 81.08 ± 0.32|
|FEAT [36] | 66.78 | 82.05|
|CNL [37] | 67.96 ± 0.98 | 83.36 ± 0.51|
|MERL [38] | 67.40 ± 0.43 | 83.40 ± 0.28|
|Deep EMD v2 [13] | 68.77 ± 0.29 | 84.13 ± 0.53|
|PAL [8] | 69.37 ± 0.64 | 84.40 ± 0.44|
|inv-equ [39] | 67.28 ± 0.80 | 84.78 ± 0.50|
|CSEI [40] | 68.94 ± 0.28 | 85.07 ± 0.50|
|COSOC [9] | 69.28 ± 0.49 | 85.16 ± 0.42|
|EASY 2×ResNet12 1sqrt(2)(ours) | 70.63 ± 0.20 | 86.28 ± 0.12 |

**TieredImageNet Dataset**

|  Methods  | 1-Shot 5-Way | 5-Shot 5-Way |   
|:--------:|:------------:|:------------:|
| Method 1 |     00.00    |     00.00    |
| method 2 |     **00.00**    |     **00.00**    |
| method 3  |     **00.00**    |     **00.00**    | 
| method 4 |     **00.00**    |     **00.00**    | 

**CUBFS Dataset**

|  Methods  | 1-Shot 5-Way | 5-Shot 5-Way |   
|:--------:|:------------:|:------------:|
| Method 1 |     00.00    |     00.00    |
| method 2 |     **00.00**    |     **00.00**    |
| method 3  |     **00.00**    |     **00.00**    | 
| method 4 |     **00.00**    |     **00.00**    | 


**CIFAR-FS Dataset**

|  Methods  | 1-Shot 5-Way | 5-Shot 5-Way |   
|:--------:|:------------:|:------------:|
| Method 1 |     00.00    |     00.00    |
| method 2 |     **00.00**    |     **00.00**    |
| method 3  |     **00.00**    |     **00.00**    | 
| method 4 |     **00.00**    |     **00.00**    | 

**FC-100 Dataset**

|  Methods  | 1-Shot 5-Way | 5-Shot 5-Way |   
|:--------:|:------------:|:------------:|
| Method 1 |     00.00    |     00.00    |
| method 2 |     **00.00**    |     **00.00**    |
| method 3  |     **00.00**    |     **00.00**    | 
| method 4 |     **00.00**    |     **00.00**    | 

## Acknowledgment


