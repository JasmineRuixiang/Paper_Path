# Paper_Path

This is a repo for important papers that shape my scientific views of computational neuroscience and neuroengineering (especially Brain Computer Interfacing).


### Population Dynamics
1) __Neural Population Dynamics during Reaching__: Ever since [Mark Churchland 2012](https://www.nature.com/articles/nature11129) (introducing jPCA, rotations) who found out the unexpected rotational structures as the underlying topology of reaching behaviors, population studies on dynamics of neural data have been put into mainstream neural data analysis.


2) __Neural Constraints on Learning__  [Patrick Sadtler 2014](https://www.nature.com/articles/nature13665) (FA+Kalman decompositions, their intrinsic space definitions (CMU/Pittsburgh is different from BrainGate), Byron Yu et al. used a different approach to estimate the intrinsic manifold (not transforming the data but using the data to find out the intrinsic manifold) _Thoughts: perturbations within and outside ---- seems like an intermediary zone between science and engineering_ ). But the issue I personally think of with CMU/Pittsburgh models is that the latent factors/intrinsic space has no temporal information in it. But one key idea of the "intuitive mapping" is significant: we will NOT directly map between neural activities and cursor kinematics!!! Instead between them there's a layer of latent factors. It's by such separation that we now have two layers that the researchers eventually could conduct 2 kinds of perturbations.

3) [Ricky Chen et al 2019](https://arxiv.org/abs/1806.07366) NeuralODE, a brilliant idea of replacing the dynamics function with a neural network. Also introduced the adjoint sensitivity method for training. NeuralODE has sed light also on normalizing flows and latent ODE, a VAE-based time series latent dynamical models. The advantages of NeuralODE are: 0) A new way of thinking about neural networks; 1) Continuous modeling instead of discrete; 2) Memory saving for training by adjoint sensitivity; 3) Continuous instead of discrete thus could handle irregular time series; 4) Normalizing flows; 5) Adaptive by user choice of ODE solvers.

4) __Latent ODEs for Irregularly-Sampled Time Series__ [Rubanov, et al 2019](https://arxiv.org/abs/1907.03907) "generalize RNNs to have continuous-time hidden dynamics defined by ordinary differential equations (ODEs), a model we call ODE-RNNs. Furthermore, we use ODE-RNNs to replace the recognition network of the recently-proposed Latent ODE model". The advantages of latent ODE models are "First, it explicitly decouples the dynamics of the system (ODE), the likelihood of observations, and the recognition model, allowing each to be examined or specified on its own. Second, the posterior distribution over latent states provides an explicit measure of _uncertainty_, which is not available in standard RNNs and ODE-RNNs. Finally, it becomes easier to answer non-standard queries, such as making predictions backwards in time, or conditioning on a subset of observations." With the underlying ODE solvers applied, ODE-RNNs an latent ODE models could handle irregularly sampled time points pretty well. To summarize, there are three features mentioned in this paper: 1) Turning from discreteness to _continuity_ (fix time gaps): from standard RNNs to ODE-RNN, because we have ODE solvers; 2) _Uncertainty_ : Using a VAE model with the latent being sampled from a Gaussian; 3) _Irregular_ time points: using an ODE solver!!!! (Point 1 and Point 3 are essentially the same thing!!). The latent ODE model perform well on _extrapolation_. 

5) __Neural Trajectories in the Supplementary Motor Area and Motor Cortex Exhibit Distinct Geometries, Compatible with Different Classes of Computation__: 
[Russo and Churchland 2020](https://www.sciencedirect.com/science/article/pii/S0896627320303664) studied the behavior of supplementary motor area (SMA) under the central hypothesis that SMA computations would internally track motion context (the choice of the cycle task is clever). They used low dimensional projections to illustrate the differences in trajectories of M1 and SMA and analyzed the subspace overlaps the different projections took. Specifically, they brought up the method of neural trajectory divergence and calculated that SMA trajectories had low divergence as expected. It's also inspiring that they used ANN and simulations to corroborate their conclusions. In the end it's enjoyment to read their discussions whether dynamical systems view would be interpreted with any assigned representations.

6) __Learning identifiable and interpretable latent models of high-dimensional neural activity using pi-VAE__ : [Zhou et al 2020](https://arxiv.org/abs/2011.04798) 's approach of hybrid models (label --- latent --- observation) is interesting though not too much science corroborated. The enlightenment this paper endows is its finding that its model pi-VAE seems to find subspaces which encode movement directions (spatial information) and neural dynamics (temporal evolution) by visualizing different combinations latent dimensions, which adds to the debate of whether the low dimensional latent space indeed "represents" anything. It also mentions GIN (General Incompressible-flow Network)

7) __Modeling behaviorally relevant neural dynamics enabled by preferential subspace identification__ [Sani et al 2021](https://www.nature.com/articles/s41593-020-00733-0): They developed a new model called PSID, which uses both neural activity and behavior in training data and prioritizes extracting behaviorally relevant neural dynamics. It turns out out that PSID learned latent factors with much less dimensions and encode behaviorally related latent dimensions with higher accuracy with fewer training samples. Surprisingly, PSID finds oppositely orientated latent trajectories for reach and return movements while other models encode the trajectories with the same orientation (Sup video 1 for further reflections). Towards the end, the authors also talked about the potential usage of PSID even to two different sources of brain signals to extract common dynamics! Be sure to understand the logic (the idea of projection and SVD to find behaviorally related representations!!) of PSID model! This paper reminds again to 1) focus on block design of models; 2) reflect deep on the relationships among neural signals, latent states, and behaviors

8) __Dynamical flexible inference of nonlinear latent factors and structures in neural population activity__ [Abbaspourazad 2023](https://www.nature.com/articles/s41551-023-01106-1) devised the DFINE mode which could do flexible inference (both noncausal smoothing and causal filtering) with missing observation values. Specifically, this model achieves better neural and behavioral predictions results and learned more robustly the underlying manifolds. The key point of the paper is that DFINE makes a two-layer structure: a nonlinear manifold latent factor, and an underlying linear dynamical latent factor, and train them together. The reflection is that we should think in terms of blocks of model and do forceful alignment.

9) __Expressive dynamics models with nonlinear injective readouts enable reliable recovery of latent features from neural activity__ [Versteeg et al 2023](https://pubmed.ncbi.nlm.nih.gov/37744459/#:~:text=Expressive%20dynamics%20models%20with%20nonlinear,latent%20features%20from%20neural%20activity) developed a model they called ODIN which conducts approximately injective mapping from latent space to neural space (so all changes in latent dynamics would necessarily affect neural states). This is specifically done by importing Neural ODE and techniques similar to invertible ResNets. Implementation of normalizing flows ensure the "approximate injectivity". Notice that unlike LFADS, ODIN cannot take non-autonomous inputs. This paper first introduces me to normalizing flows (injectivity) and I see the first time Neural ODE applied in population latent dynamics models. Furthermore, ODIN uses three different implementations for dynamics and mapping, which illustrate how making a model is similar to building Lego blocks.



### Review Papers
1) __Neural Manifolds for the Control of Movement__: [Gallego et al 2017](https://pubmed.ncbi.nlm.nih.gov/28595054/) emphasized 1) the connections between neural connectivity and the constrained and thus low dimensional latent variable manifold; 2) neural modes in motor cortices(1] population variability in PMd is reduced by stimulus presentation, 2] the timeline of studies on the orthogonal potent/null spaces for movement and preparatory activities); 3) learning and connectivity which affect the latent manifold (1] CMU Sadtler & Byron Yu perturbation and learning within/outside of latent space, 2]Sussilo training RNN to represent learning, 3] balanced neural networks also exhibited oscillatory behaviors)

2) __Latent Factors and Dynamics in Motor Cortex and Their Application to Brain–Machine Interfaces__: 
[Pandarinath et al 2018](https://www.jneurosci.org/content/38/44/9390) A well-written review which taught me several things: 0) "First, it predicts that the initial conditions of the system, such as those observed during move- ment preparation, largely determine the subsequent evolution of activity. Second, the activity of neurons in MC should relate not only to the inputs and outputs of the system, but also to the computations being performed. Finally, distinct computations may be appropriated into different, non-overlapping neural dimensions" ---- the final point might be illustrated by output-potent/output-null factors; 1) not all neural activities are directly related to inputs/outputs; they might be related to other aspects of computations (e.g., dealing with entangling or the Existence of a condition-invariant signal for transitioning from movement preparation to generation); 2) Different methods for modeling: 1] trial averaging + low dimensional projection (PCA, dPCA); 2] To not average trial, do FA or TCA; 3] To explicitly model dynamics, we could do GPFA, LDS-based models, or RNNs(LFADS); 3) Could use latent dynamics modeling to both increase BMI performance (e.g., Even Chen paper to explicitly model errors) or extending BMI longevity (Could use DAD or GAN when there's lack of supervised alignment)

3) __Interpreting neural computations by examining intrinsic and embedding dimensionality of neural activity__ [Jazayeri, Ostojic 2021](https://www.sciencedirect.com/science/article/pii/S0959438821000933) wrote a review paper. Specifically, they differentiated embedding dimensionality and intrinsic dimensionality, the former encoding the way all the sensory and movement inputs are processed, while the latter encoding the latent variables themselves. Notice the paper's discussions on orthogonal subspace, model generalization, and controllability. It's also worth attention how the authors emphasized the role of recurrent dynamics in latent feature extractions. At the end, the authors briefly mentioned methods for model reductions: 1) Model distillation; 2) Mean-field analysis (especially to directly extract latent variables from RNN!)

4) __Preparatory activity and the expansive null-space__ [Churchland 2024](https://www.nature.com/articles/s41583-024-00796-z) illustrated Churchland's thoughts on the distinction between output-potent and output-null subspaces. They theorized on how rotatory behaviors might be explained from the perspective of the null-space theory (rotations give the null-space possibility to handle preparatory activities), and how cycling might reduce neural entangling. The flexibility-via-subspace hypothesis is informative for experiment design and hypothesis generations.



