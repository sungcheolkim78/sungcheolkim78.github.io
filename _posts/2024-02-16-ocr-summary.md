---
title: 'OCR for Korean language'
date: 2024-02-16
category: ML
tags:
  - image process
  - OCR
---


## What is OCR (Optical Character Recognition)? 

사진 속에 있는 글자들을 인식해서 컴퓨터가 사용할 수 있는 텍스트로 변환하는 기술

![](/images/ocr_general_workflow.png)

1. preprocessing: 기울기 보정, 얼룩 제거, 손상된 이미지 복구, example: Histogram equlization
1. text detection: object detection -> confirm text exists, bounding box and angle
1. text recognition: text and coordinates, CRNN 
1. restructuring: 검출된 좌표에 따라서 문자를 재배치하여 원래 이미지와 비슷한 구조로 생성 

## Test with 8 OCR services

1. https://github.com/tesseract-ocr/tesseract
1. https://github.com/JaidedAI/EasyOCR
1. https://cloud.google.com/vision/docs?hl=ko
1. https://aws.amazon.com/ko/pm/textract/?gclid=CjwKCAiA9ourBhAVEiwA3L5RFl6-iGNO26zqRjsiFk_ycVbJf5QiF5aVtYA0bEfB2Ttm5jsROaJkxBoC4BIQAvD_BwE&trk=ba68822c-4d74-4f28-b470-bb363c226519&sc_channel=ps&ef_id=CjwKCAiA9ourBhAVEiwA3L5RFl6-iGNO26zqRjsiFk_ycVbJf5QiF5aVtYA0bEfB2Ttm5jsROaJkxBoC4BIQAvD_BwE:G:s&s_kwcid=AL!4422!3!658520966096!!!g!!!19852661900!149878733980
1. https://learn.microsoft.com/en-us/azure/ai-services/document-intelligence/overview?view=doc-intel-4.0.0
1. https://www.ncloud.com/product/aiService/ocr
1. https://www.upstage.ai/document-ai/overview
1. https://github.com/PaddlePaddle/PaddleOCR

## Comparisons (for Korean text recognition)

- (Speed) GoogleCloudVision > Tesseract > Upstage > NaverClova
- (Korean) NaverClova > Upstage > Azure Document > Google Vision 
- Recommendation: Azure Document, NaverClova 

## How to measure the OCR algorithm

- Accuracy: comparision between original text and recognized text
- Character Error Rate (CER): character by accuracy
- Word Error Rate (WER): word by accuracy
- check this link [post](https://towardsdatascience.com/evaluating-ocr-output-quality-with-character-error-rate-cer-and-word-error-rate-wer-853175297510)

## What is CRNN architecture?

- layers: Convolution Layers + Recurrent Layers + Transcription Layers 
- backbone: VGG-16 model 
- CNN layer -> last 2 FC into CNN -> LSTM(RNN) layer 
- CRNN parameters: input shape (256, 32, 1), num_classes (87)
- output shape: (Non, 62, 87)

## Data preparation

- VGG Image Annotator (https://gitlab.com/vgg/via)
