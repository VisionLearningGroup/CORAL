Correlation Alignment for Domain Adaptation
========

Welcome to the website of CORAL framework. CORrelation ALignment or CORAL in short is a simple yet effective method for unsupervised domain adaptation. CORAL minimizes domain shift by aligning the second-order statistics of source and target distributions, without requiring any target labels. There are mainly three parts of the CORAL framework. In the [CORAL paper](http://www.aaai.org/ocs/index.php/AAAI/AAAI16/paper/download/12443/11842) (reference 1 in the Citation Section below), we describe a solution that applies a linear transformation to source features to align them with target features before classifier training. For linear classifiers, we propose to equivalently apply CORAL to the classifier weights, leading to added efficiency when the number of classifiers is small but the number and dimensionality of target examples are very high. The resulting [CORAL Linear Discriminant Analysis (CORAL-LDA)](https://github.com/UMassLowell-Vision-Group/bmvc2014/raw/master/bmvc14_paper.pdf) (reference 2 in the Citation Section below) outperforms LDA by a large margin on standard domain adaptation benchmarks. Finally, we extend CORAL to learn a nonlinear transformation that aligns correlations of layer activations in deep neural networks (DNNs). The resulting [Deep CORAL](https://arxiv.org/abs/1607.01719) (reference 3 in the Citation Section below) approach works seamlessly with DNNs and achieves state-of-the-art performance on standard benchmark datasets.

Source Code and Data
--------------
1. CORAL: the source code is in code/CORAL_Source_Code.zip, the data used in reference 1 is included in /dataset folder
2. CORAL-LDA: the code and data can be found [here](https://github.com/UMassLowell-Vision-Group/From-Virtual-to-Reality)
3. Deep-CORAL: the source code is in code/D-CORAL.zip, the data used is the standard Office31 dataset

Tips for (Visual) Domain Adaptation
--------------
The following tips are based on my (Baochen Sun) personal experience and discussions (in person or via email) with others. I found them to be extremely useful to design/apply domain adaptation algorithms yet seldom mentioned/explained in the literature. I put them here and hope it helps :-)

1. Data Processing for Domain Adaptation
---------
Data processing is very importrant for domain adaptation applications even though it is seldom mentioned (or not emphasised enough) in the literature. It is extremely true for ''shallow'' approaches as many of them (i.e., CORAL) are doing asymmetric transformation (applying transformation to source/target only). For example, suppose we normalize BOTH the source AND target to have the same distribution (i.e., zero mean and unit variance). Then after the asymmetric transformation, the distribution of the transformed source is going to be different to the target. To achieve good performance on the target data, the distribution on which the classifier/detector is trained on need to be as close to the target as possible. We used the same trick (please refer to the SVM_Accuracy function in Ex_CORAL.m) as SA to ensure this. The most commonly used data pre-processing approach for visual domain adaptation is l1 normalization and zscore (the one used in the source code of CORAL,SA, GFK, etc.). l2 normalization also works pretty well (or even better than l1/zscore) on deep features (for the 'shallow'' methods). For deep methods, as the raw image is feeded into the network and same/similar transformations are applied to BOTH source AND target data, there is little need of extra data processing. 

2. Domain Adaptation Equilibrium
---------
As EXPLICITLY mentioned in [Deep CORAL](https://arxiv.org/abs/1607.01719), there is an equilibrium between aligning the distributions (between the source and target) and keeping the discriminative power of the features (i.e., high classification accuracy). ''Minimizing the classification loss itself is likely to lead to overfitting to the source domain, causing reduced performance on the target domain. On the other hand, minimizing the CORAL loss alone might lead to degenerated features. For example, the network could project all of the source and target data to a single point, making the CORAL loss trivially zero.'' This equilibrium is also IMPLICITLY used in many ''shallow'' methods in a different way. For example, constraining the transformation to be linear can be think of an IMPLICIT way of regularization. 

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
    Author={Baochen Sun and Kate Saenko},
    Title={From Virtual to Reality: Fast Adaptation of Virtual Object Detectors to Real Domains},
    Booktitle={BMVC},
    Year={2014}
}
```

3. Deep CORAL
```
@inproceedings{dcoral,
  author={Baochen Sun and Kate Saenko},
  title={Deep CORAL: Correlation Alignment for Deep Domain Adaptation},
  booktitle={ECCV 2016 Workshops},
  year={2016}
}
```

FAQ
--------------
Please send your further questions to baochens AT gmail DOT com 

