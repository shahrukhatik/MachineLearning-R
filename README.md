# Nearest Neighbor Algorithm

   This repository with deal with the application of k-nn Algorithm to diagnose breast cancer using R. The following process has been adapted from Brett Lantz, "Machine Learning With R". The following process will adapt to using the nearest neighbor algorithm to correctly attempt predict whether the patients had a benign or malignant tumor.

# I. Introduction 

Let us figure out the effectiveness of whether detecting cancer by applying the k-NN algorithm to measurements of biopsied cells 
from women with abnormal breast masses. The dataset, "Wisconsin Breast Cancer Diagnostic" can be found from the <a href="http://archive.ics.uci.edu/ml.">UCI Machine Learning Repository</a>. Browse through the area untill you see "Breast Cancer Wisconsin (Diagnostic) Data Set" on the right hand side. Click on the data folder and download "wdbc.data". This if the file we will be working with. If you would like a better explanation of the dataset and variables please click the "Data Description" tab.
The dataset contains 569 observations, with 32 attributes. The first 12 contain Patient ID, cancer type and then:
<ul><li>Radius</li>
<li>Texture</li>
<li>Perimeter</li>
<li>Area</li>
<li>Smoothness</li>
<li>Compactness</li>
<li>Concavity</li>
<li>Concave points</li>
<li>Symmetry</li>
<li>• Fractal dimension</li></ul>
The later attributes are just variants of the preceeding 10, such as Radius_StandardError or Radius Worst. 

# II. Exploring and Transforming the Dataset

The first step would be to import the data. You may import the data using the 'Import Dataset' button if you have RStudio installed, or use the following code:

     > wbcd <- read.csv("wisc_bc_data.csv", stringsAsFactors = FALSE)

I suggest renaming the dataset afterwards, to ease out complex issues that may arise when you are trying to tell the variables a part. In order to this we will use the colnames() function. To understand the data and variables better, consider looking through the file data description in the same place you found the data. I have renamed this dataset using the data descriptions found.

    colnames(wdbc) <-c("diagnosis","radius_mean","texture_mean","perimeter_mean","area_mean","
    smoothness_mean","compactness_mean","concavity_mean","concavepnts_mean","symmetry_mean",
    "fractal_mean","radius_SE","texture_SE","perimeter_SE","area_SE","smoothness_SE","compactness_SE",
    "concavity_SE","concavepts_SE","symmetry_SE","fractal_SE","vradiuse_worst","texture_worst",
    "perimeter_worst","area_worst","smoothness_worst","compactness_worst","concavity_worst",
    "concave_worst","symmetry_worst","fractal_worst")

If you have done everything correctly you should see that your data fram has 569 obs. of 32 varaibles. As we don't need the 'ID' for this problem, we can decide to drop it.

    wbcd <- wbcd[-1]

Many R machine learning classifiers require that the target feature is coded as a factor, so we will need to recode the diagnosis variable. 

    > wbcd$diagnosis<- factor(wbcd$diagnosis, levels = c("B", "M"),
       labels = c("Benign", "Malignant"))

Observing the prop.table() output,
    > round(prop.table(table(wbcd$diagnosis)) * 100, digits = 1)
     Benign Malignant
      62.7 37.3 #result

