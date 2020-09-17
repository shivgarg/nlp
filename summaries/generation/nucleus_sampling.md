The paper discusses the generation procedure from language models. Two main problems of quality and diversity in text generation are considered. The authors propose a sampling procedure based on probability mass. The conclusions which are drawn in the paper are: 

1.    Beam search assigns higher scores to degenerate/repetitive sequence of tokens leading to poor quality generation.  

2.    Pure sampling leads to incoherent text, leading to poor quality text. This is due to unreliable tail distribution. 

3.    Temperature scaling leads to less diversity in the text being generated 

4.    To mitigate above issues, Nucleus sampling is proposed to balance both diversity and quality. 

Nucleus sampling tries to overcome the shortcomings associated with top-k sampling (repetitive/incoherent issues) and temperature scaling (diversity issue).  Nucleus sampling creates a smallest possible set of tokens with probability mass greater than a threshold(p). 

The experiments to back the claims are sound. The evaluation is done using five metrics: Perplexity, Self-BLEU4, Zipf Coefficient, repetition % and HUSE. A couple of different sampling techniques have been compared against each other alongwith human generated text and the eval results show the balance nucleus sampling tries to achieve between quality/diversity tradeoff. 

I am not sure of the argument that the natural language does not stay in the high probability area of text generation.  The authors use this argument to justify the poor performance of beam search. Maybe this is an artifact of the language modelling unable to capture long term dependency and nuanced token semantics. I believe most of the human text uses commonplace words only.  

The authors argue that the generated text perplexity should be close to the perplexity of human generated text. I did not see any motivation/insight behind this argument, would love to hear about this. Moreover, the task of predicting probability threshold is analogous to picking k in top k or temperature in temperature scaling.  

Overall, the paper is well written with extensive quantitative and qualitative experiments with previous approaches. I find the approach to be simple enough that can be applied to any method and intuitive enough due to some parallels with top-k sampling approach.  