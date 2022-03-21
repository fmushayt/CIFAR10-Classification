# PyTorch: ResNet for CIFAR10 image classification

My best model was  ResNet with 3Blocks per layer, and no dropout with a testing accuracy of 0.8170.

 - FcNet                      - Training time: 0m 57s   Training Accuracy: 0.3134   Testing Accuracy: 0.3550


 - ConvNet                 - Training time:  4m 18s    Training Accuracy:   0.5036   Testing Accuracy: 0.5602


 - RN_1Block            - Training time: 10m 3s     Training Accuracy: 0.7286   Testing Accuracy: 0.7156


 - RN_1Block_drop   - Training time: 11m 42s  Training Accuracy: 0.6788   Testing Accuracy: 0.6975


 - RN_2Block            - Training time: 13m 47s   Training Accuracy: 0.8266   Testing Accuracy: 0.7968


 - RN_2Block_drop   - Training time: 13m 48s   Training Accuracy: 0.7711   Testing Accuracy: 0.7764


 - RN_3Block            - Training time: 16m 30s   Training Accuracy: 0.8481   Testing Accuracy: 0.8170


 - RN_3Block_drop   - Training time: 16m 2s     Training Accuracy: 0.7999   Testing Accuracy: 0.8148


In general, I noticed increasing the number of blocks increases the accuracy. Although the jump in accuracy when I went from 2 to 3 blocks was not as big as when I went from 1 to 2. 

Another interesting thing I noticed is increasing the batch size significantly reduces training time, but usually slightly reduces accuracy as well. My assumption is this is due to the normalization factors being more meaningful for smaller batch sizes. In the end, I chose the middle ground with a batch size of 64

Dropout did not improve the accuracy of any of my models, in fact tended to reduce testing accuracy. However, after implementing the validation set, I observed clearly that it does indeed tend to reduce overfitting, as the difference between training and validation loss was smaller with dropout. 

I implemented the Validation set, as well as tried training with RMSProp and Adam in addition to SGD.

Surprisingly, a larger learning rate achieved better accuracy when training ResNet with SGD. However a smaller lr tends to overfit less. The best result was when I set lr=0.1 which boosted the accuracy to 0.8522. It was the opposite for Adam and RMSProp which had the best results when lr=0.01. Blue line is the validation line below.

