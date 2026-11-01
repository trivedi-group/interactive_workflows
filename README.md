# Interactive machine learning workflows for chemometrics

Visual, widget based machine learning workflows for chemometric analysis, developed by the Trivedi Research Group at the University of Manchester. The workflows are built in Orange, a data mining tool in which each step of an analysis is a widget on a canvas and data flow along the links between them. They cover data cleaning, exploratory analysis, feature ranking and the training and validation of classification models, and can be followed without writing any code.

## What is in the repository

Each `.ows` file is an Orange workflow.

* `boxplots.ows` loads a dataset, filters samples with Select Rows, removes unused values with Purge Domain, chooses variables with Select Columns and draws box plots to compare variables between groups.
* `bigsvm workflow.ows` is a complete analysis. Data are filtered, cleaned and pre-processed, then explored without supervision through principal component analysis (PCA) with a score plot, multidimensional scaling (MDS) and Louvain clustering. The data are then split with Data Sampler into training and test sets. Support vector machine (SVM) and random forest classifiers are trained and evaluated with Test & Score and a confusion matrix, and variables are ranked using the random forest.
* `bigsvm workflow copy.ows` is a variant that compares five classifiers (SVM, random forest, k nearest neighbours, classification tree and naive Bayes). Variables ranked by Rank are passed through Select Columns so that models are trained and tested on the selected features only. Results are shown as a confusion matrix, ROC curves and box plots of the top ranked variables.
* `variable selected training.ows` pre-processes and splits the data, ranks variables, and trains and tests models on the selected variables. It evaluates two parallel Test & Score set ups, each with its own confusion matrix and ROC analysis, so that model performance can be compared before and after variable selection.
* `SVM_new_volatiles.ows` trains SVM and random forest models on one file and tests them on a separate, independently loaded file, giving an external validation. Both files are filtered and harmonised with Select Rows, Edit Domain and Purge Domain so that their variables match. Results are reported as a confusion matrix, ROC curves and a table of predictions. `SVM_new_volatiles copy.ows` is an identical copy.

## Requirements

* Orange 3 (Orange Data Mining), available for Windows, macOS and Linux from https://orangedatamining.com
* No programming is needed. A working knowledge of Python is helpful if you want to extend Orange with scripts or add-ons.

## Using the workflows

1. Install and open Orange.
2. Choose File, then Open, and select one of the `.ows` files.
3. The input data are not included in this repository. Double click each File widget and load your own dataset. Orange reads CSV, tab delimited and Excel files. Place the class or group label in its own column and set it as the target variable in the File widget.
4. Check the settings in Select Rows, Select Columns, Edit Domain and Preprocess, as these were set for the original datasets and will need changing for yours.
5. Open any widget to inspect its output. Changes flow through the workflow automatically.

Be aware of the limitations of each machine learning method you choose. Always check model performance on independent test data, and remember that classification models trained on small sample sets can overfit.

## References

Demšar J, Curk T, Erjavec A, Gorup Č, Hočevar T, Milutinovič M, Možina M, Polajnar M, Toplak M, Starič A, Štajdohar M, Umek L, Žagar L, Žbontar J, Žitnik M, Zupan B. Orange: data mining toolbox in Python. Journal of Machine Learning Research. 2013, 14, 2349 to 2353.

## Licence

Released under the GNU General Public License v3.0. See `LICENSE` for the full text.
