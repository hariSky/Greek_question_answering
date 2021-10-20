# Greek question answering BERT approach

Design of a greek question-answering NLP system based on pretrained bert model

The bert model used for finetuning and the tokenizer are from the following source 
https://github.com/nlpaueb/greek-bert

The dataset consists of pairs of questions and answers gathered on the web.
The model was finetuned using bert at "question-answering" mode.

Part of general training of bert is next sentence prediction.

This task is performed in order to learn connections between sentences. From the available text corpora, sentence pairs are formed. Whenever the pairs are subsequent in the original text, a IsNext label is attached to them. Whenever the sentence pairs are not subsequent in the original texts, a NotNext label is attached.

Based on that principle, question-answering models can be generated by finetuning bert on a relatively small dataset of question-answer pairs.

<a href="https://github.com/hariSky/Greek_question_answering/imgs/bertimgs.png">Facebook DETR's detection</a>.


Automatic localization and classification of thoracic abnormalities from chest radiographs for the VinBigData Chest X-ray Abnormalities Detection Kaggle competition using <a href="https://github.com/facebookresearch/detr">Facebook DETR's detection</a>.

<a href="https://github.com/stamatelou/DETR_object_detection/blob/main/detr_architecture.jpg"><img src="https://github.com/stamatelou/DETR_object_detection/blob/main/detr_architecture.jpg"   ></a>    


<b><H3> Input Datasets: </b> </H3>
A) <b> Image dataset:</b> <a href="https://www.kaggle.com/corochann/vinbigdata-chest-xray-original-png?select=train_meta.csv">(test and train folder)</a>  
18000 images (train set: 15000 images, test set: 3000 images)

The image dataset includes 14 types of thoracic abnormalities from chest radiographs as well as images with no abnormality detected (no finding). The different labels are as follows: <br/>
0 - Aortic enlargement <br/>
1 - Atelectasis <br/>
2 - Calcification <br/>
3 - Cardiomegaly <br/>
4 - Consolidation <br/>
5 - ILD <br/>
6 - Infiltration <br/>
7 - Lung Opacity <br/>
8 - Nodule/Mass <br/>
9 - Other lesion <br/>
10 - Pleural effusion <br/>
11 - Pleural thickening <br/>
12 - Pneumothorax <br/>
13 - Pulmonary fibrosis <br/>
14 - No finding <br/>

B) <b>Image metadata</b>  <a href="https://www.kaggle.com/c/vinbigdata-chest-xray-abnormalities-detection/data">(train.csv)</a>  
the train set metadata, each row represents an abnormality of one image, its class and bounding box. Some images can contain multiple abnormalities.

<b> <H3> Prerequisites:</b></H3>
Running the DETR model requires the use of a GPU and <b> Kaggle's notebook environment </b> can provide that. <br/>
The code of this repository can be also found in <a href="https://www.kaggle.com/stamatelou/detr-thoracic-abnormalities-detection"> this Kaggle's public notebook</a>.


For the training: <br/>
1) Select the mode = 'train'<br/>
1) Add data --> Competitions Data --> Search for "VinBigData Chest X-ray Abnormalities Detection"<br/>
2) Add data --> Datasets --> Search for "vinbigdata-chest-xray-original-png"<br/>
3) Enable the GPU in the Settings --> Accelarator --> GPU<br/>
The output of the mode is "detr_model.pth"<br/>

For the predictions: <br/>
1) Select the mode = 'predict'<br/>
2) Go to the outputs of the previous version (train mode "detr_model.pth"), select "New dataset" and keep the created URL<br/>
3) Go back to Kaggle's notebook --> Add data --> Datasets --> Search by URL with the saved URL from the last step<br/>
4) Εnable the CPU in the Settings --> Accelarator --> CPU<br/>

<b><H3>Results: </b> </H3>

Learning curve<br/>
<a href="https://github.com/stamatelou/DETR_object_detection/blob/main/training_validation_curve.jpg"><img src="https://github.com/stamatelou/DETR_object_detection/blob/main/training_validation_curve.jpg"  width="350" ></a>   

Mean average precision <br/>
<a href="https://github.com/stamatelou/DETR_object_detection/blob/main/map_curve.jpg"><img src="https://github.com/stamatelou/DETR_object_detection/blob/main/map_curve.jpg"  width="350" ></a>    
                                                                                                                              
