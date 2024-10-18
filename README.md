# Audio Feature Extraction from Spectrograms in Python

This project focuses on extracting various audio features from a given audio file using **spectrograms**. A spectrogram is a visual representation of the audio signal's frequencies over time. Using the Python library `librosa`, we can extract multiple features from the audio signal or its spectrogram. These features help in analyzing the sound for tasks such as speech recognition, music classification, and more.

## Extracted Audio Features and Their Meanings

### 1. **Mel-Spectrogram**

- **What It Is**: A Mel-spectrogram represents the power of the sound across various frequencies over time, but on the **Mel scale**, which mimics human perception of sound, focusing more on lower frequencies.
- **Why It's Useful**: It is a fundamental representation of sound, commonly used for tasks like speech recognition and music genre classification.

### 2. **MFCCs (Mel-Frequency Cepstral Coefficients)**

- **What It Is**: MFCCs are coefficients that capture the shape of the spectral envelope (how the power of the sound varies with frequency).
- **Why It's Useful**: These coefficients are widely used in speech and music analysis, providing a compact representation of the spectral properties of the audio.

### 3. **Spectral Centroid**

- **What It Is**: The spectral centroid represents the "center of mass" of the frequency spectrum.
- **Why It's Useful**: It indicates the **brightness** of the sound. Higher values generally correspond to "brighter" sounds with more high frequencies.

### 4. **Spectral Bandwidth**

- **What It Is**: Spectral bandwidth measures the width of the frequency spectrum.
- **Why It's Useful**: It provides a sense of how spread out the frequencies in the sound are, useful for distinguishing between different kinds of sounds (e.g., noisy vs. tonal).

### 5. **Chroma STFT (Short-Time Fourier Transform)**

- **What It Is**: Chroma features represent the distribution of the 12 pitch classes (C, C#, D, etc.) in the audio.
- **Why It's Useful**: These features are helpful for music analysis as they capture harmonic and melodic structure.

### 6. **Spectral Contrast**

- **What It Is**: Spectral contrast captures the difference in amplitude between peaks and valleys in the spectrum.
- **Why It's Useful**: It helps to distinguish between harmonic content and noise, and can provide insights into the "texture" of the sound.

### 7. **RMS (Root Mean Square Energy)**

- **What It Is**: RMS energy represents the loudness or power of the signal over time.
- **Why It's Useful**: It indicates the dynamic range and intensity of the audio signal, giving information about how loud the sound is.

### 8. **Zero-Crossing Rate**

- **What It Is**: The zero-crossing rate measures how frequently the signal crosses the zero amplitude line.
- **Why It's Useful**: A higher zero-crossing rate indicates noisier, percussive sounds, while lower rates are associated with more tonal sounds.

## How We Extract These Features

Using **`librosa`** in Python, we can extract all of these features directly from the audio signal or its spectrogram. Below is a simplified outline of the process:

1. **Load the Audio File**: We first load the audio file into memory using `librosa.load()`, which returns the waveform and sample rate.
2. **Compute the Spectrogram**: For features like the Mel-spectrogram, we compute the spectrogram using `librosa.feature.melspectrogram()`.
3. **Extract Features**: Each feature (MFCCs, spectral centroid, etc.) is computed using corresponding `librosa` functions.
4. **Store the Features**: These features are stored and can be used for further analysis or machine learning tasks.

```python
import librosa

# Load the audio
y, sr = librosa.load('your_audio_file.mp3')

# Extract features
mfccs = librosa.feature.mfcc(y=y, sr=sr, n_mfcc=13)
spectral_centroid = librosa.feature.spectral_centroid(y=y, sr=sr)
chroma_stft = librosa.feature.chroma_stft(y=y, sr=sr)
spectral_contrast = librosa.feature.spectral_contrast(y=y, sr=sr)
```
