The paper presents a dataset for open domain tablet-to-text generation task. The task is important because as it allows to test models on the ability to reason and numerical inference. Moreover, neural models have been found to hallucinate which is somewhat harder to evaluate given current eval metrics, but having structured data makes the process a bit easier.  The dataset is one of the largest datasets of the type with 120K train, 7.7K val/test instances. The topics distribution follows a long tail distribution.  The number of unique tables is 83K with median 87 cells per table and 3 median highlighted cells per table. The authors follow a two-stage annotation process: 

* Stage one: 

    1.    Parsed Wikipedia articles and fetched sentences tables pairs with numeric values matching or cell values matching or are hyperlinked to a table. 

    2.  Table Readability: Example deleted if the table is unreadable. 

    3. Cell Highlighting: Highlights cells that is present in the sentence or is logically inferred from the sentence.  

    4. Phrase deletion: delete phrases in sentences having no mention in the cell. NO grammatical correction allowed at this stage. 

    5. Decontextualization: Sentence can be changed to add missing context, like pronouns referring to info in the earlier of paragraph. 

* Stage two: Sentences modified to correct for fluency and grammatical errors. 

The baselines are standard approaches utilizing transformers and seq2seq architecture.  The authors pretty good ablation studies with these baselines giving potential hard cases the dataset has, with the substantial gap in test and train split depicting a lot of scope in modelling. The challenges lie in model hallucinating info, changing table structure, rare topics, requirement of numerical reasoning. 

 

Questions: 

1.    I did not understand the motivation of a separate second stage. Why phrase deletion phase in stage one could not do the sentence structure correction too? 

2.    How to interpret BLEU scores apart from the fact that the agreement drops? 

3.    The paper mentions that 82% sentences require reference to metadata. But why is that needed? In the phrase deletion phase, all such information would have been removed from the sentence. 

4.    Why low frequency header values have been removed from the dataset? Would not it help to evaluate on generalizability, given the rare topics have been listed as a challenge. 

5.    One thing, I would have liked was to use existing SOTA on existing datasets and comparing the performance gap in the existing datasets. Maybe, existing dataset show even higher performance gaps. 