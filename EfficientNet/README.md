# EfficientNet Keras (and TensorFlow Keras)
Table of Content 

1. [About EfficientNet]
2. [Implementation on Keras] 
3. [Example on a real Dataset]

1. [About EfficientNet]

Convultional neural network are developed at a fixed resource budget then it comes the fine-tuning and scaling phase for better accuracy , in the EfficientNet paper
the empirical studies shows that it is unavoidable to scale up width/depth/resolution in a balanced way , in order to do that ,they propose a simple effective compoud scaling method , this method scales uniformly network width , depth , resolution , with a set of fixed scaling coefficients  , the authors of the paper claim that we can achieve better accuracy in case we search the best fit of width , depth , resolution separatly , but the search becomes infeasible and high expensive 

<table border="0">
<tr>
    <td>
     <img src=https://user-images.githubusercontent.com/47725118/129231751-9de3c3b9-bbfe-4045-8314-c3210401ccf3.png ,width="100%" />
      </td>
    <td>  
     <img src=https://user-images.githubusercontent.com/47725118/129231881-4d3ec1e6-768e-4aa1-aead-c72d2332e176.png, width="90%" />
    </td>
</tr>
</table>
EfficientNet achieve the state-of-the-art with a better FLOPS (floating point operations) which means less operations are required to run a single instance the model , better accuracy and less parameters , what else !!!!

2. [Implementation on Keras] 

## Implementation on Keras 

loading the base base model
```python
# models can be build with Keras or Tensorflow frameworks
# we commonly use the  imagenet pre-trained weights , so this parameter allows us to do some transfer learning 
#include_top allows us to manually change the final layer to our costum layer 
#classes allows us to define the number of classes to classify images into , but only if we set include_top to True
conv_base = EfficientNetB6(weights="imagenet", include_top=False, input_shape=input_shape , classes = num_classes )

```
connfiguring the model 
```python
 
model = models.Sequential()
model.add(conv_base)
model.add(layers.Flatten())
model.add(layers.Dense(16, activation="relu"))
model.add(layers.Dense(8, activation="relu"))
#model.add(layers.Dropout(rate=0.2))
# Set NUMBER_OF_CLASSES to the number of your final predictions.
model.add(layers.Dense(1, activation="sigmoid"))
```

3. [Example on a real Dataset]

you can find the Example notebook below 
