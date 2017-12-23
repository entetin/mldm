Machine Learning and Data Mining

Home assignment 2


Train a plain feedforward conv net on classification problem, then the modified architecture and compare the results.

* HW2.ipynb

(0.125) change non-linearity of convolutional layers to sigmoid;
(0.125) change non-linearity of convolutional layers to ELU;

* HW2star.ipynb

(1.0*) make convolution kernel to be block tensor (like BlockConv2D exercise). The simplest way to do approximately the same thing is to use one of the following architectures instead of one convolution layer:
concatLayer([ incoming -> conv1x1(m) -> conv3x3(m) for _ in range(k) ]);
i.e. break n-filter conv into k branches (m = n / k), in each branch the first conv1x1 selects n / k channels, the following convs processes it, then everything is assembled back by ConcatLayer or ElementwiseSumLayer..

block-net.png (attached) depicts all three options for breaking kernel of conv(16) into 4 blocks (ElementwiseMergeLayer performs elementwise sum).
Initialize last conv layers in each branch with gain=1.0 / k
