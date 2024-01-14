[![name](https://colab.research.google.com/assets/colab-badge.svg)]([[https://colab.research.google.com/github/knc6/jarvis-tools-notebooks/blob/master/jarvis-tools-notebooks/ChemNLP_Example.ipynb]](https://colab.research.google.com/drive/1FRayOxp07ReOUUrL7ZXkPTmF1Ocu5ygI?usp=sharing))
![alt text](https://github.com/usnistgov/chemnlp/actions/workflows/main.yml/badge.svg)
[![DOI](https://zenodo.org/badge/523320947.svg)](https://zenodo.org/badge/latestdoi/523320947)

# Chemistry-NLP

# New Releases
* Text classification using different algorithms
* Feature selection
* Dimosionality reduction
  
# Table of Contents
* [Introduction](#intro)
* [Installation](#install)
* [Examples](#example)
* [Web-app](#webapp)
* [Reference](#reference)

<a name="intro"></a>
Introduction
-------------------------
Chemistry-NLP is a software-package to process chemical information from the scientific literature.

<p align="center">
   <img src="https://github.com/zaki1003/Chemistry-NLP/blob/develop/chemnlp/Schemcatic.PNG" alt="ChemNLP"  width="600"/>
</p>

<a name="install"></a>
Installation
-------------------------
First create a conda environment:
Install miniconda environment from https://conda.io/miniconda.html
Based on your system requirements, you'll get a file something like 'Miniconda3-latest-XYZ'.

Now,

```
bash Miniconda3-latest-Linux-x86_64.sh (for linux)
bash Miniconda3-latest-MacOSX-x86_64.sh (for Mac)
```
Download 32/64 bit python 3.8 miniconda exe and install (for windows)
Now, let's make a conda environment, say "Chemistry-NLP", choose other name as you like::
```
conda create --name Chemistry-NLP python=3.9
source activate Chemistry-NLP
```
#### Method 1 (using setup.py):

Now, let's install the package:
```
git clone https://github.com/zaki1003/Chemistry-NLP.git
cd Chemistry-NLP
python setup.py develop
cde data download
```

#### Method 2 (using pypi):

As an alternate method, Chemistry-NLP can also be installed using `pip` command as follows:
```
pip install chemnlp
cde data download
```


<a name="classification"></a>
Classification
---------
For classification I tried 7 classification algorithms: SVC, MLPClassifier, RandomForestClassifier, DecisionTreeClassifier, Logistic, XGBoost, KNN, MultinomialNB. 

### Feature selection in text classification:
Feature selection is one of the most important steps in the field of text classification. As text data mostly have high dimensionality problems. To reduce the curse of high dimensionality, feature selection techniques are used. The basic idea behind feature selection is to keep only important features and remove less contributing features.

Issues associated with high dimensionality are as follows:

1. Adds unnecessary noise to the model

2. High space and time complexity

3. Overfitting


The feature selection techniques we used in our project are: 

the Chi-Square feature selection: The Chi-square test is used in statistics to test the independence of two events. More specifically in feature selection, we use it to test whether the occurrence of a specific term and the occurrence of a specific class are independent.

f_classif : Compute the ANOVA F-value between label/feature for classification tasks.

mutual_info_classif : Estimate mutual information for a discrete target variable

### Dimosionality reduction in text classification:
In the field of Natural Language Processing (NLP), analyzing and processing vast amounts of text data can be challenging. Dimensionality reduction techniques come to our rescue by simplifying the data and extracting meaningful information.

The dimosionality reduction technique we used in our project is: 
TruncatedSVD: This transformer performs linear dimensionality reduction by means of truncated singular value decomposition (SVD). Contrary to PCA, this estimator does not center the data before computing the singular value decomposition. This means it can work with sparse matrices efficiently. And it works efficiently on count/tf-idf vactors.

**NB**: The PCA didn't work because it does not support sparse input.


### Classification Results:
|                |          original data      |      chi-square   |           mutual_info_classif      |          f_classif         | Trunced SVD |      
|:-------------------|:---------------|:--------------|:-------------|:-----------|:------------------|
|         SVC      |          **0.94**      |     0.15       |        0.754        |        0.382           |      0.120            |                    
|       MLPClassifier        |            **0.94**          |         **0.158**         |      **0.756**        |        **0.424** | 10.1 | 

|       RandomForestClassifier        |            **0.94**          |         0.158         |     0.756        |        0.424 | 10.1 | 

|       Logistic regression        |            **0.92**          |         **0.158**         |      **0.756**        |        **0.424** | 10.1 | 


|       XGBoost        |            **0.90**          |         **0.158**         |      **0.756**        |        **0.424** | 10.1 | 



|       KNN        |            0.53          |         **0.158**         |      **0.756**        |        **0.424** | 10.1 | 


|       MultinomialNB        |            **0.89**          |         **0.158**         |      **0.756**        |        **0.424** | 10.1 | 







<a name="example"></a>
Examples
---------
#### Parse chemical formula 

```
run_chemnlp.py --file_path="chemnlp/tests/XYZ"
```

#### Text classification example

```
python chemnlp/classification/scikit_class.py --csv_path chemnlp/sample_data/cond_mat_small.csv
```

[Google Colab example for installation and text classification](https://colab.research.google.com/github/knc6/jarvis-tools-notebooks/blob/master/jarvis-tools-notebooks/ChemNLP_Example.ipynb)

#### Text generation example

[Google Colab example for Text Generation with HuggingFace](https://colab.research.google.com/github/knc6/jarvis-tools-notebooks/blob/master/jarvis-tools-notebooks/ChemNLP_TitleToAbstract.ipynb)


<a name="webapp"></a>
Using the webapp
---------
The webapp is available at: https://jarvis.nist.gov/jarvischemnlp

![JARVIS-ChemNLP](https://github.com/usnistgov/chemnlp/blob/develop/chemnlp/PTable.PNG)

<a name="reference"></a>
Reference
---------


[ChemNLP: A Natural Language Processing based Library for Materials Chemistry Text Data](https://arxiv.org/abs/2209.08203)
