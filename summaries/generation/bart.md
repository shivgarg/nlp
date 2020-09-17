BART presents a denoising autoencoder pretrained model which is trained by corrupting text and learning a sequence to sequence model to reconstruct the corrupted source text. The introduction of autoregressive decoder provides the flexibility to apply various noising schemes, as the decoder output length is independent of the input length. The decoder transformer is based on GPT and the encoder transformer is based on BERT. The decoder has a cross-attention layer to attend on outputs of last layer on the encoder. Five types of input corruption are used: 

1.    Token Masking: Like BERT 

2.    Token Deletion: Token deleted instead of being replaced with MASK token 

3.    Text Infilling: Like SpanBert, each span replaced with a single MASK token , instead of n MASK tokens. 

4.    Sentence Permutation: Like in XLNet. 

5.    Document Rotation: pivoting input wrt to a token. 

The paper did extensive ablation studies to study the effect of various noising techniques. The text infilling gave the best performance on the downstream tasks. BART outperformed all the existing techniques, with worse performance on ELI5 abstractive QA task. The larger version of the model is competitive with RobertA on discriminative tasks with superior performance on summarisation, dialogue, QA and machine translation. The summarisation performance gain is upto 6 ROUGE points.  The results are promising, combining both generative and discriminative tasks under the same model.  

Questions/Concerns: 

1.    Token Masking: Loss in the encoder or in the decoder layer or in both places? 

2.    What is the motivation of using token masking in presence of Token Deletion? I feel masking is subproblem of the deletion task. 

3.    Why in classification tasks, only decoder representation not enough? Fine tuning is being done anyway. Maybe we can just pass all zeros vector as encoder outputs. 

4.    Training info missing, like how frequently the above noising techniques were applied?  

5.    Why both sentence permutation and document rotation? The results do not show much benefit of using both noising techniques.  

6.    Why sentence permutation necessary? Since all the context is available through encoder heads. Though positional embedding will be different, still the tokens are available at each time from the encoder output. XLNet used to build context wrt to succeeding tokens. 

7.    Rotation special case of sentence permutation (like if we choose sentence starting token as start) 

8.    ELI5 trends not clear, performs poorly on small model but outperforms other approaches on larger model. The justification given that the information contained in context may be insufficient is not well understood by me and some elaboration would have been beneficial. 

9.    No details of the “Best System” for ConvAI2 dataset. 

A promising direction to explore is using the architecture for multitask training, such as QA modelling (Discriminative) and explanation generation for why the answer satisfies the question. Maybe use encoder for discriminative task and decoder for generative tasks. 

 

 