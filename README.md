# Alcohol-Detection-SVM-classifier-based-on-PPG-signal
This repository contains code based on article 'Non-invasive detection of alcohol concentration based on photoplethysmogram signals'  The full paper quoted by this project may be read at arXiv.org, ResearchGate, and Academia.edu.

## Methods

#### PPG peak and valley detection algorithm
Peaks and valleys of PPG signals are detected by 'find_peaks' from scipy.signal.
Additionally, this method will be replaced by 'Adaptive threshold method for the oeak detection' for more accurate detection.


#### Remove base line drift
Detected valleys are interpolated by 'CubicSpline' from scipy.interpolate in order to decide a base line.
Then, original signal is subtracted by the base line.


#### Get an average cycle
To equalize the length of cycles, cropped cycles are padded by zeros and averaged.
However, this method can make one of the featrue 'the depth of valley' weaker. So I`m trying to change the code to extract features in first, and then average featrues of all cycles.


#### Extract features
According to article[1], three features are used to train classifier.
1. rotation angle
2. curvature sum
3. depth of valleys


#### SVM based mancine learning
SVM based classifier 'SVC' from sklearn.svm is used. It will be displaced by tensoflow based classifier.


## References
[1] Chen, Y. Y., Lin, C. L., Lin, Y. C., & Zhao, C. (2017). Non-invasive detection of alcohol concentration based on photoplethysmogram signals. IET Image Processing, 12(2), 188-193.

[2] Shin, H. S., Lee, C., & Lee, M. (2009). Adaptive threshold method for the peak detection of photoplethysmographic waveform. Computers in biology and medicine, 39(12), 1145-1152.
