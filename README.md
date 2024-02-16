# Paper_Path

This is a repo for important papers that shape my scientific views of computational neuroscience and neuroengineering (especially Brain Computer Interfacing).


### Population Dynamics
1) _Neural Population Dynamics during Reaching_: Ever since [Mark Churchland 2012](https://www.nature.com/articles/nature11129) (introducing jPCA, rotations) who found out the unexpected rotational structures as the underlying topology of reaching behaviors, population studies on dynamics of neural data have been put into mainstream neural data analysis.


2) _Neural Constraints on Learning_  [Patrick Sadtler 2014](https://www.nature.com/articles/nature13665) (FA+Kalman decompositions, their intrinsic space definitions (CMU/Pittsburgh is different from BrainGate), Byron Yu et al. used a different approach to estimate the intrinsic manifold (not transforming the data but using the data to find out the intrinsic manifold) _Thoughts: perturbations within and outside ---- seems like an intermediary zone between science and engineering_ ). But the issue I personally think of with CMU/Pittsburgh models is that the latent factors/intrinsic space has no temporal information in it. But one key idea of the "intuitive mapping" is significant: we will NOT directly map between neural activities and cursor kinematics!!! Instead between them there's a layer of latent factors. It's by such separation that we now have two layers that the researchers eventually could conduct 2 kinds of perturbations.

3) _Neural Trajectories in the Supplementary Motor Area and Motor Cortex Exhibit Distinct Geometries, Compatible with Different Classes of Computation_: 
[Russo and Churchland 2020](https://www.sciencedirect.com/science/article/pii/S0896627320303664) studied the behavior of supplementary motor area (SMA) under the central hypothesis that SMA computations would internally track motion context (the choice of the cycle task is clever). They used low dimensional projections to illustrate the differences in trajectories of M1 and SMA and analyzed the subspace overlaps the different projections took. Specifically, they brought up the method of neural trajectory divergence and calculated that SMA trajectories had low divergence as expected. It's also inspiring that they used ANN and simulations to corroborate their conclusions. In the end it's enjoyment to read their discussions whether dynamical systems view would be interpreted with any assigned representations.

4) _Learning identifiable and interpretable latent models of high-dimensional neural activity using pi-VAE_ : [Zhou et al 2020](https://arxiv.org/abs/2011.04798) 's approach of hybrid models (label --- latent --- observation) is interesting though not too much science corroborated. The enlightenment this paper endows is its finding that its model pi-VAE seems to find subspaces which encode movement directions (spatial information) and neural dynamics (temporal evolution) by visualizing different combinations latent dimensions, which adds to the debate of whether the low dimensional latent space indeed "represents" anything. It also mentions GIN (General Incompressible-flow Network) 


### Review Papers
1) _Neural Manifolds for the Control of Movement_: [Gallego et al 2017](https://pubmed.ncbi.nlm.nih.gov/28595054/) emphasized 1) the connections between neural connectivity and the constrained and thus low dimensional latent variable manifold; 2) neural modes in motor cortices(1] population variability in PMd is reduced by stimulus presentation, 2] the timeline of studies on the orthogonal potent/null spaces for movement and preparatory activities); 3) learning and connectivity which affect the latent manifold (1] CMU Sadtler & Byron Yu perturbation and learning within/outside of latent space, 2]Sussilo training RNN to represent learning, 3] balanced neural networks also exhibited oscillatory behaviors)


