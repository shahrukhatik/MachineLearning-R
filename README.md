# Nearest Neighbor Algorithm

   This repository with deal with the application of k-nn Algorithm to diagnose breast cancer using R. The following process has been adapted from Brett Lantz, "Machine Learning With R". The following process will adapt to using the nearest neighbor algorithm to correctly attempt predict whether the patients had a benign or malignant tumor.

# I. Introduction 

Let us figure out the effectiveness of whether detecting cancer by applying the k-NN algorithm to measurements of biopsied cells 
from women with abnormal breast masses. The dataset, "Wisconsin Breast Cancer Diagnostic" can be found from the <a href="http://archive.ics.uci.edu/ml.">UCI Machine Learning Repository</a>. 

The dataset contains 569 observations, with 32 attributes. The first 12 contain Patient ID, cancer type and then:
• Radius
• Texture
• Perimeter
• Area
• Smoothness
• Compactness
• Concavity
• Concave points
• Symmetry
• Fractal dimension
The later attributes are just variants of the preceeding 10, which you will see later while following along.

