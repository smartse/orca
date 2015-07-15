# orca

![ORCA logo](doc/orca_small.png) ORCA (Ordinal Regression and Classification Algorithms) is a MATLAB framework including a wide set of ordinal regression methods associated to the paper "Ordinal regression methods: survey and experimental study" published in IEEE Transactions on Knowledge and Data Engineering. If you use this framework please cite the following work:

```
P.A. Gutiérrez, M. Pérez-Ortiz, J. Sánchez-Monedero, F. Fernández-Navarro and C. Hervás-Martínez (2015), "Ordinal regression methods: survey and experimental study", IEEE Transactions on Knowledge and Data Engineering. Vol. Accepted
```

Bibtex entry:

```
@Article{Gutierrez2015,
  Title                    = {Ordinal regression methods: survey and experimental study},
  Author                   = {P.A. Guti\'errez and M. P\'erez-Ortiz and J. S\'anchez-Monedero and  F. Fernandez-Navarro and C. Herv\'as-Mart\'inez},
  Journal                  = {IEEE Transactions on Knowledge and Data Engineering},
  Year                     = {2015},
  Volume                   = {Accepted}
}
```

For more information about the paper and the ordinal datasets used please visit the associated webpage: http://www.uco.es/grupos/ayrna/orreview
For more information about our research group please visit [Learning and Artificial Neural Networks (AYRNA) website](http://www.uco.es/grupos/ayrna/index.php/en) at [University of Córdoba](http://www.uco.es/) (Spain).

The code is mainly composed of the following folders and files:
- [doc](doc): Folder containing the documentation (class diagrams and example of use). There is a [How to tutorial](doc/orca-tutorial.md) to get started. Other tutorials are:
  - [Use ORCA with HTCondor](orca/doc/orca-condor.md)
  - [Paralelize ORCA experiments](orca/doc/orca-condor.md)
- [src](src): Folder containing the matlab code.

The [src](src) folder contains the following folders and files:
- [Algorithms](src/Algorithms): Folder containing the matlab classes for the algorithms included and the original code (if applicable). The algorithms included in ORCA are the followings:
 - [SVC1V1](src/Algorithms/SVC1V1.m) [1]: Nominal Support Vector Machine performing the OneVsOne formulation (considered as a naïve approach for ordinal regression since it ignores the order information).
 - [SVC1VA](src/Algorithms/SVC1VA.m) [1]: Nominal Support Vector Machine with the OneVsAll paradigm (considered as a naïve approach for ordinal regression since it ignores the order information).
 - [SVR](src/Algorithms/SVR.m): Standard Support Vector Regression with normalised targets (considered as a naïve approach for ordinal regression since the assumption of equal distances between targets is done).
 - [CSSVC](src/Algorithms/CSSVC.m): This is a nominal SVM with the OneVsAll decomposition, where absolute costs are included as different weights for the negative class of each decomposition (it is considered as a naïve approach for ordinal regression since the assumption of equal distances between classes is done).
 - [SVMOP](src/Algorithms/SVMOP.m): Binary ordinal decomposition methodology with SVM as base method, it imposes explicit weights over the patterns and performs a probabilistic framework for the prediction.
 - [ELMOP](src/Algorithms/ELMOP.m): Standard Extreme Learning Machine imposing an ordinal structure in the coding scheme representing the target variable.
 - [POM](src/Algorithms/POM.m): Extension of the linear binary Logistic Regression methodology to Ordinal Classification by means of Cumulative Link Functions.
 - [SVOREX](src/Algorithms/SVOREX.m): Ordinal formulation of the SVM paradigm, which computes discriminant parallel hyperplanes for the data and a set of thresholds by imposing explicit constraints in the optimization problem.
 - [SVORIM](src/Algorithms/SVORIM.m): Ordinal formulation of the SVM paradigm, which computes discriminant parallel hyperplanes for the data and a set of thresholds by imposing implicit constraints in the optimization problem.
 - [SVORLin](src/Algorithms/SVORLin.m): We have also included a linear version of the SVORIM method (considering the linear kernel instead of the Gaussian one) to check how the kernel trick affects the final performance (SVORLin).
 - [KDLOR](src/Algorithms/KDLOR.m): Reformulation of the well-known Kernel Discriminant Analysis for Ordinal Regression by imposing an order constraint in the projection to compute.
 - [REDSVM](src/Algorithms/REDSVM.m): Augmented Binary Classification framework that solves the Ordinal Regression problem by a single binary model (SVM is applied in this case).
 - [ORBoost](src/Algorithms/ORBoost.m): This is an ensemble model based on the threshold model structure, where normalised sigmoid functions are used as the base classifier. The *weights* parameters configures whether the All margins versions is used (`weights=true`) or the Left-Right margin is used (`weights=false`).



- [condor](src/condor): Folder with the necessary files and steps for using condor with our framework.
- [config-files](src/config-files): Folder with different configuration files for running all the algorithms.
- [Measures](src/Measures): Folder with the matlab classes for the metrics used for evaluating the classifiers.
- [Algorithm.m](src/Algorithm.m): File that sets the necessary properties and functions for an algorithm class.
- [DataSet.m](src/DataSet.m): Matlab class for data preprocessing.
- [Experiment.m](src/Experiment.m): Matlab class that runs the different experiments.
- [Metric.m](src/Metric.m): File that sets the necessary properties and functions for a metric class.
- [Utilities.m](src/Utilities.m): Class that preprocess the experiment files, run the different algorithms and produces the results.

# References
[1] C.-W. Hsu and C.-J. Lin, “A comparison of methods for multi-class support vector machines,” IEEE Transaction on Neural Networks, vol. 13, no. 2, pp. 415–425, 2002.
[2] A. Smola and B. Schölkopf, “A tutorial on support vector regression,” Statistics and Computing, vol. 14, no. 3, pp. 199–222, 2004.
[3] E. Frank and M. Hall, “A simple approach to ordinal classification,” in Proceedings of the 12th European Conference on Machine Learning, ser. EMCL ’01. London, UK: Springer-Verlag, 2001, pp. 145–156.
[4] W. Waegeman and L. Boullart, “An ensemble of weighted support vector machines for ordinal regression,” International Journal of Computer Systems Science and Engineering, vol. 3, no. 1, pp. 47–51, 2009.
[5] J. Cheng, Z. Wang, and G. Pollastri, “A neural network approach to ordinal regression,” in Proceedings of the IEEE International Joint Conference on Neural Networks (IJCNN2008, IEEE World Congress on Computational Intelligence). IEEE Press, 2008, pp. 1279–1284.
[6] W.-Y. Deng, Q.-H. Zheng, S. Lian, L. Chen, and X. Wang, “Ordinal extreme learning machine,” Neurocomputing, vol. 74, no. 1–3, pp. 447– 456, 2010.
[7] P. McCullagh, “Regression models for ordinal data,” Journal of the Royal Statistical Society. Series B (Methodological), vol. 42, no. 2, pp. 109–142, 1980.
[8] M. J. Mathieson, “Ordinal models for neural networks,” in Proceedings of the Third International Conference on Neural Networks in the Capital Markets, ser. Neural Networks in Financial Engineering, J. M. A.-P. N. Refenes, Y. Abu-Mostafa and A. Weigend, Eds. World Scientific, 1996, pp. 523–536.
[9] W. Chu and S. S. Keerthi, “Support Vector Ordinal Regression,” Neural Computation, vol. 19, no. 3, pp. 792–815, 2007.
[10] B.-Y. Sun, J. Li, D. D. Wu, X.-M. Zhang, and W.-B. Li, “Kernel discriminant learning for ordinal regression,” IEEE Transactions on Knowledge and Data Engineering, vol. 22, no. 6, pp. 906–910, 2010.
[11] W. Chu and Z. Ghahramani, “Gaussian processes for ordinal regression,” Journal of Machine Learning Research, vol. 6, pp. 1019–1041, 2005.
[12] H.-T. Lin and L. Li, “Reduction from cost-sensitive ordinal ranking to weighted binary classification,” Neural Computation, vol. 24, no. 5, pp. 1329–1367, 2012.
[13] H.-T. Lin and L. Li, “Large-margin thresholded ensembles for ordinal regression: Theory and practice,” in Proc. of the 17th Algorithmic Learning Theory International Conference, ser. Lecture Notes in Artificial Intelligence (LNAI), J. L. Balcazar, P. M. Long, and F. Stephan, Eds., vol. 4264. Springer-Verlag, October 2006, pp. 319–333. 
