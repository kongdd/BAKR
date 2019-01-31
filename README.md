# Bayesian Approximate Kernel Regression (BAKR)
Nonlinear kernel regression models are often used in statistics and machine learning due to greater accuracy than linear models. Variable selection for kernel regression models is a challenge partly because, unlike the linear regression setting, there is no clear concept of an effect size for regression coefficients. In [Crawford et al. (2018)](https://www.tandfonline.com/doi/full/10.1080/01621459.2017.1361830), we propose a novel framework that provides an analog of the effect size of each explanatory variable for Bayesian kernel regression models when the kernel is shift-invariant --- for example the Gaussian kernel. We use function analytic properties of shift-invariant reproducing kernel Hilbert spaces (RKHS) to define a linear vector space that: (i) captures nonlinear structure, and (ii) can be projected onto the original explanatory variables. The projection onto the original explanatory variables serves as an analog of effect sizes. The specific function analytic property we use is that shift-invariant kernel functions can be approximated via random Fourier bases. Based on the random Fourier expansion we propose a computationally efficient class of Bayesian approximate kernel regression (BAKR) models for both nonlinear regression and binary classification for which one can compute an analog of effect sizes. We illustrate the utility of BAKR by examining two important problems in statistical genetics: genomic selection (i.e. phenotypic prediction) and association mapping (i.e. inference of significant variants or loci). State-of-the-art methods for genomic selection and association mapping are based on kernel regression and linear models, respectively. BAKR is the first method that is competitive in both settings.

BAKR is implemented as a set of R and C++ routines, which can be carried out within an R environment. Supporting Information for Crawford et al. (2018) can be found [here](https://www.tandfonline.com/doi/suppl/10.1080/01621459.2017.1361830?scroll=top).


### The R Environment
R is a widely used, free, and open source software environment for statistical computing and graphics. The most recent version of R can be downloaded from the [Comprehensive R Archive Network (CRAN)](http://cran.r-project.org/). CRAN provides precompiled binary versions of R for Windows, MacOS, and select Linux distributions that are likely sufficient for many users' needs.  Users can also install R from source code;  however, this may require a significant amount of effort.  For specific details on how to compile, install, and manage R-packages, refer to the manual [R Installation and Administration](http://cran.r-project.org/doc/manuals/r-release/R-admin.html).


### R Packages Required for BAKR
The BAKR tutorial requires the installation of the following R libraries:

* [coda](https://cran.r-project.org/web/packages/coda/index.html)

* [doParallel](https://cran.r-project.org/web/packages/doParallel/index.html)

* [Rcpp](https://cran.r-project.org/web/packages/Rcpp/index.html)

* [RcppArmadillo](https://cran.r-project.org/web/packages/RcppArmadillo/index.html)

* [MASS](https://cran.r-project.org/web/packages/MASS/index.html)

* [BGLR](https://cran.r-project.org/web/packages/BGLR/index.html)

The easiest method to install these packages is with the following example command entered in an R shell:

    install.packages("coda", dependecies = TRUE)

Alternatively, one can also [install R packages from the command line](http://cran.r-project.org/doc/manuals/r-release/R-admin.html#Installing-packages).

### C++ Functions Required for BAKR
The code in this repository assumes that basic C++ functions and applications are already set up on the running personal computer or cluster. If not, the BAKR functions and necessary Rcpp packages will not work properly. A simple option is to use [gcc](https://gcc.gnu.org/). macOS users may use this collection by installing the [Homebrew package manager](http://brew.sh/index.html) and then typing the following into the terminal:

    brew install gcc

For macOS users, the Xcode Command Line Tools include a GCC compiler. Instructions on how to install Xcode may be found [here](http://railsapps.github.io/xcode-command-line-tools.html). For extra tips on how to run C++ on macOS, please visit [here](http://seananderson.ca/2013/11/18/rcpp-mavericks.html). For tips on how to avoid errors dealing with "-lgfortran" or "-lquadmath", please visit [here](http://thecoatlessprofessor.com/programming/rcpp-rcpparmadillo-and-os-x-mavericks-lgfortran-and-lquadmath-error/).

### Tutorial for Running BAKR
The simulation tutorial provided here is based on a simple (and small) genetics example where we simulate genotype data for n = 500 individuals with p = 2000 measured SNPs. We will randomly select a small number (e.g. 30) of these SNPs to be causal and have true association with the generated (continuous) phenotype y. In this script we walk through the basic functions of BAKR. Specifically it shows how to: (1) compute the approximate Kernel matrix and its singular value decomposition form; (2) run the Gibbs Sampler for BAKR; (3) retrieve the beta estimates for the original variants/genes/obeserved variables; (4) conduct inference and/or out-of-sample prediction.

This script also notes how functions change when the variables are binary instead of continuous.

### Relevant Publications
L. Crawford, K.C. Wood, X. Zhou, and S. Mukherjee (2018). Bayesian approximate kernel regression with variable selection. _Journal of the American Statistical Association_. **113**(524): 1710-1721.

K.R. Singleton*, L. Crawford*, E. Tsui, H.E. Manchester, O. Maertens, X. Liu, M.V. Liberti, A.N. Magpusao, E.M. Stein, J.P. Tingley, D.T. Frederick, G.M. Boland, K.T. Flaherty, S.J. McCall, C. Krepler, K. Sproesser, M. Herlyn, D.J. Adams, J.W. Locasale, K. Cichowski, S. Mukherjee, K.C. Wood (2017). Melanoma therapeutic strategies that select against resistance by exploiting MYC-driven evolutionary convergence. _Cell Reports_. **21**(10): 2796-2812.

### Questions and Feedback
For questions or concerns with the BAKR functions, please contact
[Lorin Crawford](mailto:lorin_crawford@brown.edu), [Xiang Zhou](mailto:xzhousph@umich.edu), or [Sayan Mukherjee](mailto:sayan@stat.duke.edu).

We appreciate any feedback you may have with our repository and instructions.
