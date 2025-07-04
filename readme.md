#  RiboDecode: Deep Generative Optimization of mRNA Codon Sequences for Enhanced mRNA Translation and Therapeutic Efficacy.

## Overview
RiboDecode is a deep learning-based tool designed to optimize mRNA codon sequences to enhance mRNA translation and therapeutic efficacy. This repository provides the necessary code and resources to predict and optimize mRNA translation levels in various cellular environments.

## Environment
To set up the environment, ensure you have the following dependencies installed:

- Python=3.8.19
- torch=2.0.1
- CUDA=12.1  
- viennarna=2.6.4 
- numpy=1.24.4  
- pandas=2.0.3
- p-tqdm=1.4.0 
- matplotlib=3.7.5 
- seaborn=0.13.2

The required dependency packages will be automatically downloaded the first time you run the program.

## **Installation and Usage**

You can create a new conda environment using the following command:

```
conda create -n ribodecode python=3.8
```

Activate the environment:

```
conda activate ribodecode
```

### **TranslationModel**

Download the necessary **.whl** file from [here](https://drive.google.com/file/d/19Yyl8uUbjQn0TAA4E52ZUGBd_pb_RyW8/view?usp=sharing) and install it using:

```
pip install TranslationModel-1.1.0-py3-none-any.whl
```

To perform local testing, use the following command:

```
pred-translation --cds ATGGACGGGTAG --env HEK293T
```

* The maximum length of the coding sequence (**cds**) should not exceed 4500nt.

* Pre-configured cellular environments (**env**): **HEK293T**, **A549**, and **HeLa**. 

For custom cellular environments, use:

```
pred-translation --cds ATGGACGGGTAG --csv env_file.csv
```

Here, '**csv**' specifies the custom cellular environment file. We provide a standard template file, **env_file.csv**, with the following format:
The first column contains human gene IDs, which must remain unchanged.
The second column lists the corresponding mRNA RPKM values, provided by the user. Missing values can be replaced with 0.

If you have any questions about the TranslationModel, you can get help information by using the following command:

```
pred-translation --help
```

### **RiboDecode**

Download the necessary **.whl** file from [here](https://drive.google.com/file/d/1BVrQvO85b0HI34cWfCNtim_eG2LXSEuv/view?usp=sharing) and install it using:

```
pip install ribodecode-1.3.0-py3-none-any.whl
```

**Note**: If **viennarna** installation fails, please upgrade tothe latest GCc compiler (**≥5.0**). Alternatively,install a specific ViennaRNA version using:

```
pip install viennarna==2.6.4
```

To perform local testing, use the following command:

```
ribo-decode --cds example --cds_seq ATGGACGGGTAG --env HEK293T --mfe_weight 0 --optim_epoch 10 --alpha 100 --beta 100
```

* **cds**	is the custom name for the coding sequence.

* **cds_seq**	is the input CDS nucleotide sequence to be optimized (should not exceed 4500nt).

* Pre-configured cellular environments (**env**): **HEK293T**, **A549**, **HeLa**. 

* **mfe_weight** can be assigned a constant value ranging from 0 to 1. If 0, the model optimizes only translation. If 1, the model optimizes only MFE (Minimum Free Energy).

* **optim_epoch** can be set to any integer value as needed, representing the number of iterations for model optimization. We recommend setting optim_epoch=10.

* **alpha** and **beta** are balancing coefficients for the translation and MFE terms in the loss function. Default: 100 (sufficient for most codon sequences where translation prediction < 100 and MFE > -1000 kcal/mol). If translation prediction > 100, set alpha to 1000. If MFE < -1000 kcal/mol, set beta to 1000.


For custom cellular environments, use:

```
ribo-decode --cds example --cds_seq ATGGACGGGTAG --env custom --mfe_weight 0 --optim_epoch 10 --csv env_file.csv
```

* The parameters after **env** can be defined manually to save the environment naming method of the generated sequence.

* **env_file.csv** should follow the same format as the csv file of the TranslationModel.

**Output Format:**

The optimized sequence will be generated in **results_natural** folder and saved to the **optim_results.txt** file for each epoch (./results_natural/**env**_optim_mfe_dist-optim/**epoch_number**/samples/optim_results.txt). The results contains three columns:

1. **mRNA codon sequence**
2. **Predicted translation level**
3. **Predicted MFE**

**Note**: When **mfe_weight=0**, the software skips MFE optimization. In such cases, the values in the third column are meaningless.

## Citation
Please cite our work if you use RiboDecode in your research:

Deep Generative Optimization of mRNA Codon Sequences for Enhanced mRNA Translation and Therapeutic Efficacy.

## Version History

- **1.0 (2024-5-29)**

  Updata readme.md.
  
- **2.0 (2025-3-12)**

  Updata readme.md.

- **3.0 (2025-6-23)**

  Updata readme.md.
  
## Contact
For any questions, issues, or further assistance, please feel free to contact us via email:
wangf376@mail2.sysu.edu.cn
