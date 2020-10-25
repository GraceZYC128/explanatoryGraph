# Interpreting CNN Knowledge via an Explanatory Graph



# Introduction

This code learns an explanatory graph for a pre-trained CNN. We have tested this code using CNNs learned by the matconvnet. However, you can extend this code to CNNs learned by other platforms, e.g. the TensorFlow.

Because this code requires massive GPU computation and parallel CPU computation, I suggest you use a computer with a GPU and powerful CPUs. Please make sure that your MATLAB is compatible with parallel computing, i.e., you can ran parpool();

Note that please choose HOME --> Preferences --> General --> MAT-Files --> MATLAB Verson 7.3 or later, in order to save large MAT files.


# Citation

Please cite the following two papers, if you use this code.
1. Quanshi Zhang, Ruiming Cao, Feng Shi, Ying Nian Wu, and Song-Chun Zhu, "Interpreting CNN Knowledge via an Explanatory Graph" in AAAI 2018
2. Quanshi Zhang, Xin Wang, Ruiming Cao, Feng Shi, Ying Nian Wu, and Song-Chun Zhu, "Extracting an Explanatory Graph to Interpret a CNN" in IEEE Transactions on Pattern Analysis and Machine Intelligence, 2020. DOI:10.1109/TPAMI.2020.2992207

# How to use

Note that please set in the window of the MATLAB following "HOME --> Preferences --> MATLAB --> General --> MAT-Files --> MATLAB Version 7.3 or later." Thus, the Matlab can save large MAT files.

1) Learn explanatory graphs for CNNs learned using the CUB200 dataset

Please download the pre-trained CNN for the CUB200 dataset from https://github.com/zqs1022/pretrainedCNNforCUB , and then unzip the file to the 'pretrained_cnns' folder.

extractCNNFeatureMaps_cub200();

learn_explanatoryGraph('cub200');

showPatch('cub200'); % show image patches corresponding to each graph node

computeStability_cub(); % compare the location stability of graph nodes and the stability of CNNfilters.


2) Learn explanatory graphs for CNNs learned using the VOC Part dataset

Please download pre-trained CNNs for the VOC Part dataset from https://github.com/zqs1022/pretrainedCNNforVOC1 , https://github.com/zqs1022/pretrainedCNNforVOC2 , https://github.com/zqs1022/pretrainedCNNforVOC3 , and then unzip the file to the 'pretrained_cnns' folder.

name='bird'; % or 'cat', 'cow', 'dog', 'horse', 'sheep'

extractCNNFeatureMaps_vocpart(name);

learn_explanatoryGraph(name);

showPatch(name); % show image patches corresponding to each graph node


3) Learn explanatory graphs for other CNNs

Write your own functions of extractCNNFeatureMaps to output

3.a) CNN feature maps (save as 'roughCNN.mat')

3.b) positive samples of training images (save as 'images.mat')

3.c) your own network configurations (the configurations of VGG16,ResNet,and VAEGAN has been written in getNetParameters.m), which includes the description of the network structure. If you use networks other than VGG16/ResNet/VAEGAN, you need your own network configurations.

These files are used as the input of learn_explanatoryGraph(). Then, run learn_explanatoryGraph().

Data structures used in our MAT files are simple. You may first run our demos and check data structures used in roughCNN.mat and images.mat, to write your code.
