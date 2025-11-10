# MelanoScan - Skin cancer detector

## Introduction
Skin cancer is one of the most common cancers globally, and early detection is essential for successful treatment. However, limited access to dermatologists and diagnostic tools makes early diagnosis difficult, especially in developing regions.  

The MelanoScan project uses AI to provide an image-based detection system that identifies skin lesions as benign or malignant and classifies malignant lesions into different types. This prototype demonstrates how artificial intelligence can provide affordable, accessible, and efficient healthcare support for early skin cancer screening. 

## Method
An object detection model (link not available) was built to identify the area in an image where a skin lesion (which may or may not be cancerous) appears. This area is then passed through an image classification model2 to determine the type of cancer shown, if any. 

The object detection model was based on a database of about 100 images taken from the internet and manually annotated. It was then trained on Roboflow using the RF-DETR (Small) architecture. 
The [classification model](https://universe.roboflow.com/techguru-3vxeq/skin_lesion_classification-lyqqy) was forked from an [existing database](https://universe.roboflow.com/major-project-ylz7h/skin_lesion_classification) which was already annotated and classified into 7 different skin lesion types. It was then trained on Roboflow using the ViT Classification architecture. 

The 7 types of skin lesions are divided into 3 malignant and 4 benign lesions, listed with their abbreviations used in the dataset: 

**Malignant lesions**: 

1. Basal Cell Carcinoma (bcc) 
2. Actinic keratoses and intraepithelial carcinoma (akiec) 
3. Melanoma (mel) 

**Benign lesions**: 

1. Benign keratosis-like lesions (bkl) 
2. Dermatofibroma (df) 
3. Melanocytic nevi (nv) 
4. Vascular lesions (vasc)

## Workflow
The workflow begins with the user uploading an image of their body part with the skin lesion they wish to identify as input. This is passed to the object detection model to identify the relevant part of the image. This cropped area is passed to the classification model to determine the type of lesion. The final output is the original image with a label and box around the skin lesion with the type of cancer predicted. If no lesion is detected, the original unaltered image is returned. 

## Prototype
The full program is intended to be embedded in a mobile application called MelanoScan. This app would allow users to upload pictures of themselves for AI analysis, book appointments, and consult with medical professionals. 

A mock design and [prototype](https://www.figma.com/proto/xQFtEPojeIc4antpmmClEU/CancerScanner?node-id=1-3&t=mG0qqB8ShWtojpLF-1) of this application was built using Figma.
