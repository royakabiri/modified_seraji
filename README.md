# Modified Uppsala Persian Universal Dependency Treebank (Seraji) 
The Uppsala Persian Universal Dependency treebank (Seraji et al., 2016) has been modified to comply with the Universal Dependencies guidelines (Nivre et al., 2020) as well as Persian linguistics, using automatic and manual corrections.

The presence of annotation errors or inconsistencies is detrimental to the intended uses of treebanks, especially the UD treebanks as the main goal is to develop cross-linguistically consistent treebank annotation for various languages. Although errors might be occasionally harmless, the proliferation of errors negatively impacts both the training and evaluation of natural language processing tasks. Detecting and removing the erroneous annotation can potentially improve the performance of the parser and facilitate multilingual and multi-domain parser development as well as cross-lingual learning.

In the process of preparing the annotation guidelines and annotating the automatically parsed sentences of the Informal Persian Universal Sependency Treebank (Kabiri et al., 2022) (https://github.com/royakabiri/iPerUDT), several linguistically grounded problematic annotations in the Uppsala treebank annotation scheme we discovered. In many cases, it did not respect the UD guidelines, either. Through data analysis, therefore, we detected all the linguistically inaccurate or UD non-compliant annotations, searched for in the rest of the treebank, identified the patterns, and designed linguistic rules to fix the errors. 

# References 

Nivre, Joakim, Marie-Catherine de Marneffe, Filip Ginter, Jan Hajič, Christopher D. Manning, Sampo Pyysalo, Sebastian Schuster, Francis M. Tyers, and Dan Zeman. (2020). Universal dependencies v2: An evergrowing multilingual treebank collection. In Proceedings of the 12th Conference on Language Resources and Evaluation (LREC), 4027–4036.

Kabiri, Roya, Simin, Karimi, and Mihai Surdeanu (2022). Informal Persian Universal Dependency Treebank. (to appear)

Seraji, Mojgan, Filip, Ginter and Nivre, Joakim. (2016). Universal Dependencies for Persian. In Proceedings of the 10th International Conference on Language Resources and Evaluation (LREC), Portorož, Slovenia.

