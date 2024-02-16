---
title: 'Explain Stable Diffusion'
date: 2024-01-07
category: ML
tags:
  - generative ai
  - txt2img
  - imt2imt
---

생성형 AI에 문장을 만들어 내는 text generation, 그림을 만들어 내는 image genration, 음성/음악을 만들어내는 wave generation이 있다. 그 중 이미지 생성에 관해서는 문장으로부터 이미지를 만들어 내는 text to image 알고리즘과 하나의 이미지로부터 다른 이미지를 만들어 내는 image to image 알고리즘, 그림으로부터 관련된 문장을 만들어 내는 image to text 알고리즘, 마지막으로 그림에 특정 부분을 생성해서 채워주는 Inpainting 알고리즘이 있다. 특히나 문장으로부터 이미지를 생성해 주는 알고리즘이 많은 연구가 진행되고 있는데, 가장 유명한 알고리즘 혹은 서비스로 Midjourney, Dall-E, Stable Diffusion 등이 있다. 이 글에서는 Stable Diffusion XL 알고리즘에 대해 배워보고 그 구성요소를 이해함으로써 어떻게 prompt를 만들어서 원하는 것에 가까운 결과를 얻을 수 있을지 이야기해 보자. 

## Diffuser pakcage from Huggingface 

실제적이면서도 자세한 설명은 huggingface의 diffuser 패키지를 설명하는 페이지에서 알 수 있다. 이 글도 다음의 웹사이틀 참고해서 작성되었음을 알린다. 우선, Stable Diffusion의 대략적인 개념을 알아야 하는데, 이를 위해서는 Diffusion Model (DM)을 알아야 한다. 이미지를 생성하기 위해서는 훈련된 수많은 그림들 중에서 원하는 문장에 가까운 그림을 찾아 주거나 만들어 주는 방법이 필요하다. Diffusion Model에서는 우선 랜덤한 숫자들로 만들고자 하는 이미지 사이즈의 배열을 만들고 여기서 순차적으로 noise를 없애는 방법으로 이미지를 만들게 된다. 얼마만한 강도로 몇번의 스텝을 거쳐서 노이즈를 없애는 지에 따라 마지막 결과물이 바뀌게 된다. 이를 조정하는 것이 Scheduler이고 여기에는 다양한 알고리즘이 제시되어 왔다. Stable Diffusion XL의 경우 PNSD Scheduler가 기본으로 선택되어 진다. 다음으로 이러한 과정마다 이미지를 latent 공간으로 옮기고 노이즈를 제거하는 과정이 필요한데 여기에는 보통 Unet2D 모델이 사용되게 된다. 마지막으로 Variational AutoEncoder (VAE)를 사용하여 주어진 text에 가까운 결과를 만들고 최소화할 loss function을 만들어 내게 된다. 

## Textual Inversion

이미지를 몇장 (5장)을 주고 거기에 해당하는 가상의 워드를 만들면 이후로 이 가상의 단어를 사용해서 그림을 만들 수 있다. 이 경우 이 단어에 해당하는 그림은 원래 주어진 그림과 매우 일치하는 결과를 보여준다. 스타일로 비슷하게 만들수 있고 추가적인 단어도 설정하여 이미지를 만들 수 있다. 