# FGSM_MNIST

We're trying to make model better which is robust against to adversarial images, especially made by FGSM.
Yann LeCun's MNIST datasets are used.

We're inspired by this [tutorial](https://www.pyimagesearch.com/2021/03/08/defending-against-adversarial-image-attacks-with-keras-and-tensorflow/).

## Fine-tune modeling
1. train model with original MNIST datasets (learning rate == 0.001)
2. get adversarial images of MNIST from trained model
3. fine-tune model with adversarial images. learning rate is 0.0001 (it may be modified)
4. validate with validation set 100 epochs each models
5. results saved as a plot 

A function named
  generate_image_adversarial(args) is just interpretation of tensorflow code to pytorch code

## Results

red line  : accuracy of original MNIST imagess of fine-tuned model
blue line : accuracy of adversarial MNIST images of fine-tuned model 

1. 1-layer-linear-classifier model 
red line is accrracy of original images validated with fine-tuned model
<br><img src="https://github.com/comeeasy/FGSM_MNIST/blob/main/report/1-layer-MNIST-epochs-100.png" width="40%" height="30%" title="px(픽셀) 크기 설정" alt="RubberDuck"></img><br>

2. 3-layer-linear-classfier model
<br><img src="https://github.com/comeeasy/FGSM_MNIST/blob/main/report/3-layer-MNIST-epochs-100.png" width="40%" height="30%" title="px(픽셀) 크기 설정" alt="RubberDuck"></img><br>

3. Convnet
<br><img src="https://github.com/comeeasy/FGSM_MNIST/blob/main/report/Convnet-MNIST-epoch-100.png" width="40%" height="30%" title="px(픽셀) 크기 설정" alt="RubberDuck"></img><br>

accuracy of original MNIST images of two simple linear classfier models are not rubust. these are not stable. however Convnet has robust accuracy of original images. accuracy of adversarial images are going up to original accuracy. almost 95%! 

### fine-tunning harms linear-classifier's prediction of original data. But (at least) above simple convolutional model is robust to fine-tunning 

## Requirements

- python 3.8+
- pytorch 0.4.1+
- numpy
- tqdm

## License

MIT License

## trained model

| Name     | Description                                                              |
| -------- | ------------------------------------------------------------------------ |
| 1-layer-linear-classifier | really simple model                                     |
| 3-layer-linear-classifier | add two layer to 1-layer simple model                   |
| Convnet                   | simple convolutional model                              |

## Longer Motivation

1. VOneNet maybe boosts performance. So we're considering how apply this model to
[VOneNet](https://github.com/dicarlolab/vonenet)
