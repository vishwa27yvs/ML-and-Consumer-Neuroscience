
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

## Classification Model:
We are now creating models which can best fit the data, some of them being K-nearestneighbours and RandomForests classifier

## References:
References:
 https://raphaelvallat.com/bandpower.html
 https://www.sciencedirect.com/science/article/pii/S0957417410005695
