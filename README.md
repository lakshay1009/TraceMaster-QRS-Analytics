# TraceMaster-QRS-Analytics
A complete Python implementation of the Pan-Tompkins algorithm for QRS detection, featuring adaptive thresholding and localized Q-S sub-peak mapping for clinical duration analysis.

# ECG Precision: Pan-Tompkins & QRS Analytics

This repository features a robust Python implementation of the **Pan-Tompkins Algorithm** for real-time ECG signal processing. Unlike standard automated libraries, this toolkit provides a transparent, step-by-step pipeline from raw signal loading to clinical metric extraction.



## 🛠 The Pipeline
The project follows the classic signal processing hierarchy to isolate the QRS complex:
1. **Bandpass Filtering:** 0.5–15 Hz Butterworth filter to remove baseline wander and high-frequency noise.
2. **Derivative Operator:** A 5-point derivative kernel to highlight the steep slope of the R-peak.
3. **Squaring & Integration:** Non-linear transformation and a 150ms moving window to consolidate energy in the QRS region.
4. **Adaptive Detection:** A custom-built peak-climbing logic that calculates a floating threshold based on signal mean and dynamic range.

## 📊 Clinical Features
* **QRS Complex Mapping:** Specifically identifies the Q-valley, R-peak, and S-valley using localized search windows.
* **Heart Rate Analysis:** Calculates instantaneous and average BPM based on R-R intervals.
* **Segmented Visualization:** A robust plotting tool that handles coordinate synchronization, allowing you to "zoom" into any time-range of the recording.

## 🚀 Quick Start
```python
# Detect Peaks
r_peaks = Rpeaks_detection(filter_signal[:,0], fs)
q_peaks, s_peaks = detect_q_s(filter_signal[:,0], r_peaks, fs)

# Visualize first 10 seconds
plot_qrs_range(filter_signal, r_peaks, q_peaks, s_peaks, fs, start_sec=0, end_sec=10)
