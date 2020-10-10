The paper introduces a new task of Grounded Situation Recognition.  The task is different from the situation recognition since is requires identification of image regions corresponding to the semantic roles in the situation recognition.  The imSitu dataset is augmented by addition of bounding box annotations to the images. The task is challenging due to requirement of semantic saliency, the objects are sparse, disambiguation is needed, scale is varied, and objects may be needed to hallucinated (due to occlusion etc.).
The object categories are around 10k, with a long tail distribution, making the task of simple object detection challenging.  The task is very similar to image captioning in practice, just the output in GSR is a structured semantic summary which can be evaluated with established metrics closer to expectations.  The analysis of the dataset is good and informative. The dataset introduces conditional object semantics, i.e. in different situations, the object scale, shape changes, thus stressing on learning the object orientation to the current situation. 

The baselines model uses a RNN model used for situation recognition. The architecture is augmented to ground semantic roles into the image.  They change the object detector pipeline in the baseline to enable large scale long tail recognition.  A combination of loss functions: L1 for bounding box regression, Focal loss of object class classification, cross-entropy for verb, ground, and noun outputs.

Overall, the paper is written well, although, I feel downstream tasks could have been motivated better.  Plus, I find the baseline a bit lacking, although the authors mention the irreproducibility of the Graph Net approach to Situation Recognition, they could have done some more ablations how different parameters affect the model performance. 

Questions:
1.	Would marking bounding boxes make the situation problem a bit easier, since extra supervision has been provided to the model in the training data? Like earlier, the model must learn to figure out places to focus upon.
2.	Did not understand exactly how the FPN complexity is reduced especially after the bounding box proposal phase of the network.
3.	The baseline model is claimed to beat SOTA on the situation recognition, but I feel this is due to extra annotations being provided, and I could not find the significance of 0.39% improvement, maybe this variation comes via different init strategies. Also, the improvement is just in one category of metrics, rest all metrics have poorer numbers as compared to Graph Net. 
Future Work
1.	Combine with captioning datasets, or use one for pretraining for the other tasks, to see if there is benefit of transferring the knowledge.






