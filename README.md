# Graph-Machine-Learning-SBU-4012-final-project
## Introduction
At this project our task was to implement a GNN model in order to accurately predict molecular properties.<br>
For classification we use HIV dataset for classification and ESOL dataset for regression.<br>
these datasets can be found in [here](https://github.com/hhaji/funqg).<br>
This project implementation is provided by using DGL library and some tools from torch modules.<br>
At this project we’ll compare effectiveness of different GNN models to predict task of datasets.<br>
## About Dataset
for classification I used HIV dataset and for regression I used ESOL dataset which their details are below<br>
[Table 1: Classificaton details](https://raw.githubusercontent.com/MeysamAgah/Graph-Machine-Learning-SBU-4012-final-project/main/table%201.png)<br>
[Table 2: Regression details](https://raw.githubusercontent.com/MeysamAgah/Graph-Machine-Learning-SBU-4012-final-project/main/table%202.png)<br>
## Preprocessing
for this project in order to use DGL first we install is then we import these modules and libraries:<br>
os, dgl, NumPy, NetworkX, Torch, Torch.nn, dgl.function, torch.nn.functional, Shutil, Data loader, Cloudpickle, SKlearn.preprocessing, Math
Since size of HIV dataset is big and each model needs 20 minutes to become finished and I faced runtime crash several times this will take a time to upload

