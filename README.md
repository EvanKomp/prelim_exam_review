# prelim_exam_review
Data and notebook acting on the data for the review paper. See readme

This repository is contains some evaluating work as review for the below publication, that is concerned with predicting adsorption energies.

A. J. Chowdhury, W. Yang, E. Walker, O. Mamun, A. Heyden, and G. A. Terejanu, “Prediction of Adsorption Energies for Chemical Species on Metal Catalyst Surfaces Using Machine Learning,” J. Phys. Chem. C, vol. 122, no. 49, pp. 28142–28150, 2018, doi: 10.1021/acs.jpcc.8b09284.

./Review_SI 

	The SI exracted zip file directly from the authors, containing feature and label data. It can be found from the source: https://pubs.acs.org/doi/10.1021/acs.jpcc.8b09284
./GP_evaluation.ipynb

	Using the authors' data to train GP models on species bond counts. This is one of the authors' investigated models. The authors repeat this and average over 100 runs, while here is highlighted the result of a single test set. 
./*.png

	Figures concerning the effeect of training data size on model accuracy as well as a single optimized model predictions. This random process (based on the training data chosen) has the potential to produce a very poor model, not seen by the authors' averaging.


Required packages:

scikit-learn, pandas, numpy, seaborn, matplotlib
