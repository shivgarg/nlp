This paper tackles the problem of open vocabulary in machine translation.  Current methods for machine translation have a fixed vocabulary with about 30k-50k words. The out of vocabulary words are handled by looking up in a dictionary or by copying the word in the target(with transliteration if needed).  Paper contributions:
*	Proposes a BPE based word segmentation algorithm
*	Analyses the tradeoff between large vocabularies and large input sequences.
*	Produced subwords are interpretable when compared to existing approaches like Huffman encoding.
*	Do translation without using a back-off dictionary.

A bottom-up approach is used to combine tokens, starting with all the words split to chars and combining most frequent consecutive token pair iteratively.  Two methods are used to generate subwords:
*	Learning independent encodings for source and destination languages
*	Learning encodings for source and destination together.  Though this approach requires transliteration if the script differs.

Interesting results show that the unigram open vocabulary perform worse and there is a tradeoff between number of most frequent shortlisted words used and subwords being used. This is because the words get rarer in training set. The subwords help to avoid this issue. When unigram dictionary used, the performance is hurt too. The unigram F1 numbers show a significant jump for rare words. 
Some questions/doubts
1.	Why only 100 words analysed for justifying the hypothesis?
2.	Infrequent subword units excluded in NMT, infrequent not defined, and moreover not well motivated why infrequent excluded.
3.	More experiments to verify the subwords are orthogonal to other improvements in NMT?
4.	Some examples listed tell that the segmentation is inconsistent, but the translation is correct. Maybe the model overfits here, as it may have seen the subwords only in one context. Maybe some examples for different words could have helped.

The concept of the paper is interesting given the simplicity of the idea and the improvements demonstrated. But I guess an area of development is to develop a robust metric to evaluate the performance of MT system on rare words.  Authors gave a good overview with examples and did some ablation studies to study the effect of the approach. The paper is easy to read and well written. 
