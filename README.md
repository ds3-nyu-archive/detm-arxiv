# Time evolution of STEM topics with Dynamic Embedded Topic Modeling (work in progress)
Quynh M. Nguyen<sup> a, b</sup> and Kyle Cranmer<sup> a, c</sup>

<sup> a</sup> _Physics Department, New York University, New York 10003_

<sup> b</sup> _Applied Math Lab, Courant Institute, New York University, New York 10012_

<sup> c</sup> _Center for Data Science, New York University, New York 10011_

## Project description
Running dynamic embedded topic modeling on abstracts of arxiv articles and discover how topics in STEM change in time. This is an implementation of [Dynamic Embedded Topic Modeling](https://github.com/adjidieng/DETM) by Adji B. Dieng, Francisco J. R. Ruiz, and David M. Blei of Columbia University. 

## Get the meta data, containing abstracts 
Visit https://www.kaggle.com/Cornell-University/arxiv (json format)

## Generate embedding 
  
```
python word2vec/run_w2v.py
```
  
This will take all words from abstracts, apply nlp processing (remove stop words, remove rare words, etc) and produce vector representations of all the words (default embedding dimension = 300), and save as embed.txt.

More on word embedding is available in this paper: https://arxiv.org/pdf/1310.4546.pdf
## Clone my fork of the original [Dynamic Embedded Topic Modeling](https://github.com/adjidieng/DETM)
I have made some changes to because of runtime errors, no change to the model so far
```
git clone https://github.com/quynhneo/DETM
```

## Preprocess text data 
```
python data_undebates.py
```
(modify the path to json file appropriately)

## Run Dynamic Embedded Topic Modeling 

```
python main.py
``` 
(all setup and models settings are on top of the file)

## Plot the results
```
python plot_word_evolution.py 
```
(edit path to saved model `beta_file` on top)

**A very preliminary** result, evolution of word probability across time for eight different topics is shown in the [.png file](https://github.com/quynhneo/detm-arxiv/blob/master/detm_un_K_50_Htheta_800_Optim_adam_Clip_0.0_ThetaAct_relu_Lr_0.005_Bsz_1000_RhoSize_300_L_3_minDF_100_trainEmbeddings_1_beta.png). A lot more pruning and tuning to be done. Currently, the run time is too long, and the text has to be preprocessed more (for example the group of words including  'abstract','introduction','conclusion','method'... is learned as a topic because they always appear together)  
