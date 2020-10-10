 This paper introduces a navigation task with multiple asymmetric agents collaborating towards a common goal. This problem is different from single agent / adversarial agents domains introduced so far. The main motivation of the problem is to allow for robot deployment in real life alongside humans.  The problem is challenging as it involves modelling asymmetric agents, execute multi-step instructions, and robustness to changes in the environment. 
 
The CEREAL BAR environment has two agents, a leader and a follower, a 3D environment to collect valid sets of cards to earn points.  The agents depend on each other since leader has limited mobility but has full environment state and follower limited state of environment but more moving capability. 

The paper uses a baseline based on Visitation Prediction Network which breaks up the modelling process as generating an action plan over the map and second part of generation of a sequence of steps to be taken by follower to execute the instruction. The two stages are trained independently and finetunes together with auxiliary data points to bridge the gaps.  The first step uses a LINGUNet and models each action independently using binary logistic loss.  The second step uses a LSTM to output all steps to execute an instruction. 
The fine-tuning process involves learning to recover from drift due to error accumulation at each step.  A process like DAGGER is used to finetune the two stages trained separately.

The paper proposes a new set of problems with the framework generalizable to many real-life situations. Paper although written well was difficult to read especially the model details. The model ablation studies are quite extensive, explaining the affect of each stage.  

Questions/Future Work:
1.	Given the agent has a global view of the environment, is not the follower self-sufficient to achieve the problem. This is context of CEREAL BAR environment since they mention that the follower has full observability. 
2.	A lot of information of the environment is encoded in the input, i.e. a red card has learnt embedding at the location x, y in the input. This assumes to be too much knowledge of the environment. In robotics, structured world models (SWMs) approach has been proposed to learn about the salient positions automatically and are a good avenue to explore.
3.	The authors mention their approach is different from imitation learning. How is it different?
4.	Why two stage trained separately? Could not find how are they disconnected that inhibits end to end training.
5.	I felt the baseline is quite weak, seq2seq model ignore the visual aspect, which is quite limiting, and did not find the motivation to use it in the first place.
6.	Why weren’t the leaders generated instruction evaluated against the gold set of instructions, since the action set includes the natural language instructions as possible actions? Any metric for language generation could have been used.
