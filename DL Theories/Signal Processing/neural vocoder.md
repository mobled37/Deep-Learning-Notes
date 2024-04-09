![[neural vocoder.png]]

Red box means vocoder, which predict raw waveform audio from low resolution representation.
To analyze audio in the frequency domain, ==Short-time Fourier transform (STFT)== is performed to extract frequency components corresponding to features. Among them, the magnitude value corresponding to the size component is used to apply the ==Mel-filterbank== and **convert it to the Mel-scale**, from which the ==Mel-spectrogram== can be obtained. 

In fact, if the **magnitude value and phase value of the frequency component are known, the STFT transformation is reversible** without information loss, so the original audio can be restored. However, in the case of TTS models that usually predict and learn Mel-spectrograms, ==only the size information of the frequency component can be obtained==. Therefore, to predict the original audio, ==phase information must be predicted== and the original audio must be predicted based on this. 

- **Vocoder:** predict phase information and generate raw audio based on mel-spectrogram. 

![[neural vocoder progress.png]]
