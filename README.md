## Fashion_mnist

This repo contains the code for the fashion MNIST dataset.

Some questions that popped in my mind when I started working with CNN<br>
- input_shape of images like image width and height?<br>
ans: if the image is greyscale then we have 1 colour channel, if the image is coloured, then we have 3 coloured channels - which are Red, Green, Blue.<br>
- Does the CNN only accept the fixed input shapes?<br>
ans: Yes, it accepts only fixed input sizes. why?<br>
- what is pooling?<br>
Ans: Downsampling the feature map.<br>
- what is max pooling?<br>
Ans: From the feature map, considering the window size and stride size. As, we move through the windows, we pick the maximum number in each window. <br>
- why should we use pooling?<br>
Ans: the advantages of pooling are reduced computational cost and translation invariance<br>
- why should we flatten out the tensors and use dense layers?<br>
Ans: As the output is a classification problem, we<br>
- why should we use softmax for multiclass classification and cross entropy loss?<br>