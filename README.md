# Detecting COVID-19 in X-ray images with Azure Custom Vision

This tutorial is inspired by Adrian Rosebrock's (PyImageSearch) post ["Detecting COVID-19 in X-ray images with Keras, TensorFlow, and Deep Learning"](https://www.pyimagesearch.com/2020/03/16/detecting-covid-19-in-x-ray-images-with-keras-tensorflow-and-deep-learning/).


In this tutorial, instead of using TensorFlow and Keras, Azure Custom Vision is being used as the engine for training the Image Classification model.


The solution discussed on this tutorial is intended for educational purposes only and does not represent, in any way, a qualified medical engine for diagnosing COVID-19. 

**This tutorial is still under development and must be updated on the following days!**

# Step-by-step

## The Data

**Unhealthy pacients:**
- The COVID-19 X-ray image dataset we’ll be using for this tutorial was curated by [Dr. Joseph Cohen](https://josephpcohen.com/w/), a postdoctoral fellow at the University of Montreal.
- Dr. Cohen started collecting X-ray images of COVID-19 cases and publishing them in the [following GitHub repo](https://github.com/ieee8023/covid-chestxray-dataset).

**Healthy pacients:**
- To sample X-ray images of healthy patients, I used [Kaggle’s Chest X-Ray Images (Pneumonia) dataset](https://www.kaggle.com/paultimothymooney/chest-xray-pneumonia) and sampled X-ray images from healthy patients. There are a number of problems with Kaggle’s Chest X-Ray dataset, namely noisy/incorrect labels, but it served as a good enough starting point for this proof of concept COVID-19 detector.

We've added the data under a blob storage, following the pattern bellow:
```
/source_dir/
/source_dir/train/
/source_dir/train/healthy/
/source_dir/train/unhealthy/
/source_dir/test/
/source_dir/test/healthy/
/source_dir/test/unhealthy/
```

All the images were converted to .PNG and, if needed, resized to assure they were smaller than 4MB.

## Training the Classification Model

For training the classification model, execute [this script](./covid19xray-custom-vision.ipynb) on an Azure Databricks environment.

The script has a step-by-step guidance for this training.

**Environment details:**
- Databricks Runtime Version 6.4 *(includes Apache Spark 2.4.5, Scala 2.11)*
- Driver: Standard_F4s | Workers: 1xStandard_F4s
- Other PyPI installed packages: `azure-cognitiveservices-vision-customvision==1.0.0`

For training the classification model, execute this following script on an Azure Databricks environment.
