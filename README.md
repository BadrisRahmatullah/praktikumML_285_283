# Colon Cancer Classification using CNN

Praktikum Machine Learning A 201810370311285 & 201810370311283
Temu Kembali Citra A 201810370311285 & 201810370311283

Link Dataset : https://www.kaggle.com/andrewmvd/lung-and-colon-cancer-histopathological-images


## Konten
* [Informasi](#general-information)
* [Library](#technologies-used)
* [Features](#features)
* [Screenshots](#screenshots)
* [Setup](#setup)
* [Model](#model)
* [Project Status](#project-status)
* [Room for Improvement](#room-for-improvement)
* [Acknowledgements](#acknowledgements)
* [Contact](#contact)
<!-- * [License](#license) -->


## General Information
- Dataset yang digunakan berjudul "Lung and Colon Cancer Histopathological Images" yang merupakan dataset citra.
- Jumlah dataset 25000.
- Terbagi dalam 5 class
- kami menggunakan 2 kelas colon sebagai bahan uji dengan 10000 data

<!-- You don't have to answer all the questions - just the ones relevant to your project. -->


## Library
- Tensorflow 2.0
- Keras
- Matplotlib
- Numpy
- seaborn


## Features
#Kelas datasetnya meliputi : 
- Lung benign tissue
- Lung adenocarcinoma
- Lung squamous cell carcinoma
- Colon adenocarcinoma
- Colon benign tissue


## Screenshots
![Example screenshot](./img/sscolon.png)
<!-- If you have screenshots you'd like to share, include them here. -->


## Setup
- prepocessing step :
* Splitting data 80:19:1 (80 train, 19 test, 1 validation)
- Augmentation :
* ImageDataGenerator : 
** rescale : 1/255
** rotation range : 40
** width and height shift range : 0.2
** zoom range : 0.2
** horizontal flip
** fill mode : nearest
** color mode : RGB
* hyper parameter : Optimizer(adam), learningrate(0,000001), loss(binary_crossentrophy)
* jumlah epoch : 100
* hasil akurasi : 0.85 dengan precision(0.98), recall(0.86), f1-score(0.92)




## model
- model sequential 1 : layer, Dense, Conv2D, MaxPool2D, AveragePooling2D, GlobalMaxPool2D, GlobalAveragePooling2D, Dropout, Flatten
- Activation : elu

- model sequential 2 : Layer, Dense, Conv2D, AveragePool2D, Flatten, BatchNormalization, Dropout, AveragePool2D
- Activation : elu 
```
model = Sequential() 

model.add(InputLayer(input_shape=[250,250,3])) 
model.add(Conv2D(filters=16, kernel_size=3, strides=1, padding='same', activation='elu')) 
model.add(MaxPool2D(pool_size=2, padding='same')) 
model.add(Conv2D(filters=32, kernel_size=3, strides=1, padding='same', activation='elu')) 
model.add(MaxPool2D(pool_size=2, padding='same')) 
model.add(Conv2D(filters=64, kernel_size=3, strides=1, padding='same', activation='elu')) 
model.add(MaxPool2D(pool_size=2, padding='same')) 
model.add(GlobalMaxPool2D()) 
model.add(Flatten()) 

model.add(Dense(128, activation='relu')) 
model.add(Dense(1, activation='sigmoid')) 
```
```
model2 = Sequential()

model2.add(InputLayer(input_shape=[250,250,3]))
model2.add(Conv2D(filters=16, kernel_size=3, strides=1, padding='same', activation='elu'))
model2.add(BatchNormalization())
model2.add(AveragePool2D(pool_size=2, padding='same'))
model2.add(Conv2D(filters=32, kernel_size=3, strides=1, padding='same', activation='elu'))
model2.add(BatchNormalization())
model2.add(AveragePool2D(pool_size=2, padding='same'))
model2.add(Conv2D(filters=64, kernel_size=3, strides=1, padding='same', activation='elu'))
model2.add(BatchNormalization())
model2.add(AveragePool2D(pool_size=2, padding='same'))
model2.add(Dropout(0.25))
model2.add(Flatten())

model2.add(Dense(128, activation='elu'))
model2.add(Dropout(0.5))
model2.add(Dense(5, activation='softmax'))

```
## Project Status
Project is: COMPLETE.


## Room for Improvement
Masih banyak improve yang bisa dilakukan pada project ini, seperti.

Room for improvement:
- Model
- Preprocessing
- Data Augmentasi

To do:
- Tambah model dengan akurasi lebih baik
- Mencoba dengan jumlah data yang lebih besar
- Mengubah data augmentasi yang ada dengan data augmentasi yang lebih baik

## Acknowledgements
Give credit here.
- https://github.com/BadrisRahmatullah/praktikumML_285_283/edit/main/README.md
- Thanks to Chamisfun






