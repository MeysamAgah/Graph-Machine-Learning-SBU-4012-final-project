# Graph-Machine-Learning-SBU-4012-final-project
## Introduction
At this project our task was to implement a GNN model in order to accurately predict molecular properties.<br>
For classification we use HIV dataset for classification and ESOL dataset for regression.<br>
these datasets can be found in [here](https://github.com/hhaji/funqg).<br>
This project implementation is provided by using DGL library and some tools from torch modules.<br>
At this project we’ll compare effectiveness of different GNN models to predict task of datasets.<br>
## About Dataset
for classification I used HIV dataset and for regression I used ESOL dataset which their details are below<br>
<br>
<br>
![Table 1: Classificaton details](https://raw.githubusercontent.com/MeysamAgah/Graph-Machine-Learning-SBU-4012-final-project/main/table%201.png)<br>
<br>
<br>
<br>
![Table 2: Regression details](https://raw.githubusercontent.com/MeysamAgah/Graph-Machine-Learning-SBU-4012-final-project/main/table%202.png)<br>
## Preprocessing
for this project in order to use DGL first we install is then we import these modules and libraries:<br>
os, dgl, NumPy, NetworkX, Torch, Torch.nn, dgl.function, torch.nn.functional, Shutil, Data loader, Cloudpickle, SKlearn.preprocessing, Math<br>
Loading datasets:<br>
we upload dataset to notebook then we need to define DGLdataset classes For classification:<br>
That’s simple by having file address and using bin file we load graphs and labels and masks and globals.<br>
Then performing train and test and split according to file. we bring data from its origin location. at origin location there were 3 scaffold which represent on scaffold in dataset so we choose first one of scaffold0 and then by DGLDataset we bring train and test and validation.<br>
For regression:<br>
For regression it’s a bit harder. We need to scale data as well as loading it.<br>
performing train and test and split according to file. we bring data from its origin location. at origin location there were 3 scaffold which represent on scaffold in dataset so we choose first one of scaffold0 and then by DGLDataset we bring train and test and validation.<br>
at this step we need to scale train set using Standard Scaler from SKlearn.preprocessing which we defined earlier at defining Regression dataset class.<br>
then according to scaler which we scaled train set, we scale validation set and test set.<br>
Then we create a collate class which catch graphs, labels, masks, globals from batches tuple.<br>
Then we define loader class:<br>
For classification:<br>
then we define a loader with batch size of 64 since dataset is a bit big. we'll define 3 dataloaders for train and validation and test, batch size for each is 64 and collate_fn is according to collate we defined earlier before defining loader.<br>
For regression:<br>
we define a loader with batch size of 32 since dataset is small.<br>
we'll define 3 dataloaders for train and validation and test, batch size for each is 32 and collate_fn is according to collate we defined earlier before defining loader.<br>
Now we have a train loader and test loader and validation loader.<br>
## Model Defining
In order to have a better accuracy we try by using different model which each of them are under different condition.<br>
number of tasks in this dataset is 1 and we set number of epochs to 100 which looks enough for this kind of task. global size is 200 which represents global feature of each graph and patience is 10 which is Number of steps to wait if the model performance on the validation set does not improve.<br>
for configuration it's better to set node_feature_size to 127, edge_feature_size to 12 and hidden size to 100 in order to avoid further problems.<br>
Then since we use 2 graph models Graph Sage and GCN and since we import GCN and define Graph Sage but first let’s have a quick brief about what each of them are:<br>
<br>
<br>
![GCN](https://raw.githubusercontent.com/MeysamAgah/Graph-Machine-Learning-SBU-4012-final-project/main/GCN.png)
<br>
<br>
<br>
![GraphSAGE](https://raw.githubusercontent.com/MeysamAgah/Graph-Machine-Learning-SBU-4012-final-project/main/Graph%20SAGE.png)<br>
<br>
<br>
<br>
Now we define 20 models and here's details.<br>
<br>
<br>
<br>
![Table 3: models list](https://raw.githubusercontent.com/MeysamAgah/Graph-Machine-Learning-SBU-4012-final-project/main/table%203.png)<br>
<br>
<br>
<br>
Now we define a compute score function:<br>
For regression loss function is RMSE and for classification is ROC-AUC.<br>
Then we define a loss function to calculate loss. For regression we use MSE as criterion of loss function and for classification we use binary cross entropy.<br>
Then we define a train epoch function.<br>
Then we define a train evaluate function which its optimizer is Adam optimizer with learning rate of 0.001 for regression first we set best validation to infinity and for classification we set to 0. This is because we want to observe better accuracies after each epoch so if first best val is set to a very bad number it’ll change once model is improving. <br>
Another thing in train evaluate is patience count and that allow us to stop operation once model was now improving.<br>
After this we define a test evaluate function to evaluate model improvement on test set.<br>
## Comparison
Now it’s time to check how much accuracy each model have and compare with original model from paper.<br>
<br>
<br>
<br>

<br>
<br>
<br>
According to table 4:
best model for classification is model 00 <br>
best model for regression is model 18 which has 5 layers and using Graph SAGE and dropout is 0.1. it appears that more layers result in better accuracy and dropout doesn’t necessarily improve model and graph sage is better than GCN<br>
**Important**
Since size of HIV dataset is big and each model needs 20 minutes to become finished and I faced runtime crash several times this will take a time to upload

