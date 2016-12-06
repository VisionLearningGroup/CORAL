Correlation Alignment for Domain Adaptation
========

Welcome to the website of CORAL framework. CORrelation ALignment or CORAL in short is a simple yet effective method for unsupervised domain adaptation. CORAL minimizes domain shift by aligning the second-order statistics of source and target distributions, without requiring any target labels. There are mainly three parts of the CORAL framework. In the [CORAL paper](http://www.aaai.org/ocs/index.php/AAAI/AAAI16/paper/download/12443/11842) (reference 1 in the Citation Section below), we describe a solution that applies a linear transformation to source features to align them with target features before classifier training. For linear classifiers, we propose to equivalently apply CORAL to the classifier weights, leading to added efficiency when the number of classifiers is small but the number and dimensionality of target examples are very high. The resulting [CORAL Linear Discriminant Analysis (CORAL-LDA)](https://github.com/UMassLowell-Vision-Group/bmvc2014/raw/master/bmvc14_paper.pdf) (reference 2 in the Citation Section below) outperforms LDA by a large margin on standard domain adaptation benchmarks. Finally, we extend CORAL to learn a nonlinear transformation that aligns correlations of layer activations in deep neural networks (DNNs). The resulting [Deep CORAL](https://arxiv.org/abs/1607.01719) (reference 3 in the Citation Section below) approach works seamlessly with DNNs and achieves state-of-the-art performance on standard benchmark datasets.


Source Code and Data
--------------
1. CORAL: the source code is in code/CORAL_Source_Code.zip, the data used in reference 1 is included in /dataset folder
2. CORAL-LDA: the code and data can be found [here](https://github.com/UMassLowell-Vision-Group/From-Virtual-to-Reality)
3. Deep-CORAL: the source code is in code/D-CORAL.zip, the data used is the standard Office31 dataset


Data Processing for Domain Adaptation
--------------
Data processing is very importran for domain adaptation applications even though it is rarely mentioned (or not emphasised enough) in the literature. It is more important of ``shallow'' methods s

Domain Adaptation Equilibrium
--------------



Citation
--------------

If you find this project is useful in your research, please consider citing:

1. CORAL
```
@inproceedings{coral,
  author={Baochen Sun and Jiashi Feng and Kate Saenko},
  title={Return of Frustratingly Easy Domain Adaptation},
  booktitle={AAAI},
  year={2016}
}
```

2. CORAL-LDA
```
@inproceedings{coral-lda,
    Author = {Baochen Sun and Kate Saenko},
    Title = {From Virtual to Reality: Fast Adaptation of Virtual Object Detectors to Real Domains},
    Booktitle = {BMVC},
    Year = {2014}
}
```

3. Deep CORAL
```
@inproceedings{dcoral,
  author    = {Baochen Sun and Kate Saenko},
  title     = {Deep CORAL: Correlation Alignment for Deep Domain Adaptation},
  booktitle   = {ECCV 2016 Workshops},
  year      = {2016}
}
```

FAQ
--------------
Please send your further questions to baochens AT gmail DOT com 

