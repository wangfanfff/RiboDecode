#  RiboCode

Deep Generative Optimization of mRNA Codon Sequences for Enhanced Protein Production and Therapeutic Efficacy.

## Environment
- Python=3.8.19  
- torch=2.0.1
- viennarna=2.6.4 
- numpy=1.24.4  
- pandas=2.0.3
- p-tqdm=1.4.0 
- matplotlib=3.7.5 
- seaborn=0.13.2

The required dependency packages will be automatically downloaded the first time you run the program.

## Installation and Usage

You can create a new conda environment using the following command:

```
conda create -n ribocode-env python=3.8
```

Activate the environment：

```
conda activate ribocode-env
```

- **TranslationModel**

You can download the necessary .whl file from the following link:

https://drive.google.com/file/d/19Yyl8uUbjQn0TAA4E52ZUGBd_pb_RyW8/view?usp=sharing

To install the TranslationModel program, execute the following command:

```
pip install TranslationModel-1.1.0-py3-none-any.whl
```

After installation, use the following command to perform local testing:

```
pred-translation --cds ATGGACGGGTAG --env HEK293T
```

The maximum length of the coding sequence (CDS) should not exceed 4500. The current environment supports HEK293T, A549, and HeLa. Support for additional environments will be added gradually.

Following these instructions, you can obtain the predicted translation level of mRNA for a specific CDS sequence in a particular cellular environment.

To use a custom cellular environment, run the following command:

```
pred-translation --cds ATGGACGGGTAG --csv env_file.csv
```

Here, 'csv' specifies the custom cellular environment file. We provide a standard template file, env_file.csv, with the following format:
The first column contains human gene IDs, which must remain unchanged.
The second column lists the corresponding mRNA RPKM values, provided by the user. Missing values can be replaced with 0.

If you have any questions about the TranslationModel, you can get help information by using the following command:

```
pred-translation --help
```

- **RiboCode**

You can download the necessary .whl file from the following link:

https://drive.google.com/file/d/1An4ppVlnjG9DF7yBqYlvdTqWrZxTRPuy/view?usp=sharing

To install the RiboCode program, execute the following command:

```
pip install RiboCode-1.3.0-py3-none-any.whl
```

After installation, use the following command to perform local testing:

```
ribo-code --cds gluc --env HEK293T --mfe_weight 0 --optim_epoch 10
```

The parameter 'mfe_weight' can be assigned a constant value ranging from 0 to 1, while the optim_epoch can be specified as an integer as required.

The cds options include gluc, NGF, H1N1, with additional sequences to be made available later. Similarly, the 'env' parameter can be set to HEK293T, A549, HeLa, with support for additional environments planned for future releases. 

To use a custom cellular environment, run the following command:

```
ribo-code --cds gluc --env custom --mfe_weight 0 --optim_epoch 10 --csv env_file.csv
```

The parameters after 'env' can be defined manually to save the environment naming method of the generated sequence. 'csv' specifies the custom cellular environment file, same format as the csv file of the TranslationModel.


## Citation

Deep Generative Optimization of mRNA Codon Sequences for Enhanced Protein Production and Therapeutic Efficacy.

## History

- **1.0 (2024-5-29)**

  Updata readme.md.
  
- **2.0 (2025-3-12)**

  Updata readme.md.
