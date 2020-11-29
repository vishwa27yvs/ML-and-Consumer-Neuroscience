
## Modeling cognitive functions of consumer behaviour using computational biology, brainwave measurement technology and machine learning.

## Data Collection:
A form was prepared where the subjects had to rate the name of a cafe on the scale of 1 to 5
depending on how appealing the title was to them, there were around 43 questions of this kind.
We gathered the corresponding EEG signal data for 26 subjects, and the signal for each
response was recorded as a ‘.mff’ file.

## Data Processing:
We mostly made use of Matlab for data processing. The word preference file for each subject
was imported and loaded into the EEGlab plugin of Matlab as set files. We performed a basic
BCR filtering and removed the signals outside the range of 0.1 Hz to 30 Hz. After this we
manually removed the noisy channels that had an enormous deviation with respect to the
neighbouring channels. The removed channel was then replaced by data processed using
interpolation (interpolare channel function supported by EEG lab).
To obtain the EEG signal for each input made by the subject we divided the set file into events
each containing a particular response. For each epoch , we take [-2,0] interval as we want to
examine the EEG signals from 2s before the key is pressed for a particular preference( done
using the pop_epoch function ). The data was labelled with whatever rating was associated with
that event. Depending on these labels, we grouped all events with similar ratings. Within the
same rating we grouped the events which were of the same subject along with the question
name. This arrangement was done so that it improves the accuracy of the classification.

## Feature Extraction:
We used python libraries such as sklearn, numpy and pandas for data analysis and processing.
We used the loadmat function from sklearn to load our mat event files. Each event was a 33 x
2000 matrix, representing data for 33 different channels for 2s, as data is sampled every 1ms.
After observing frontal alpha asymmetry we shall majorly focus on the data from the channels
F1,F2,F3,F4,F11,F12 (frontal lobe).
To perform EEG signal processing we decomposed all signals into distinct frequency bands,
delta (1-3)Hz, theta (3.5,7.5)Hz , alpha (7.5,13)Hz and beta(14,30)Hz. The signals that we shall
consider for modelling behaviour are theta, alpha and beta.
By using and plotting Welch's periodogram we get the average bandpower for that signal. We
computed the total power and found out relative theta power, relative beta power and relative
alpha power. Using the Multitaper spectral analysis method we found the relative average
band power. These were the final set of features which we shall try to classify on. MNE
extensions were used for the same.

## Classification Model:
After looking at several similar research observations SVM, K nearest neighbours have been
accurately successful in their predictions on EEG data. The data frame has been resized and
normalized wherever required and we have used a 80%-20% train test split. We are still working
on developing other features and models to improve the accuracy of the model. Till now, as we
have a multiclass classification data we have made use of following algorithms and a brief
description.:-
K-Nearest Neighbours : Used K-NN with 2 neighbors and euclidean metric for distance.
Random Forests : Random Forest Model with 100 estimators, activated bootstrap and used ‘sqrt’
metric for feature selection.
Logistic Regression : Simple logistic regression metric used was accuracy.

## References:
References:
 https://raphaelvallat.com/bandpower.html
 https://www.sciencedirect.com/science/article/pii/S0957417410005695
