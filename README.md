# DL-Noise-Suppressor
This solution is to tackle the problem of noise entering the mic of the speaker causing issues in audio making it hard to hear the speaker. This solution aims to suppress the noise being broadcasted onto the meeting by using deep learning.  


Using Deep learning, we can remove some of the unwanted bundles of frequencies by representing the audio files as STFTs or Short Term Fourier Transform. This input format can be represented as an image which are posted below.  

The architecture which is being used for this solution is the UNet model which was originally designed for edge detection tasks in medical imaging. Since spectrograms are also a form of an image, we can utilise this architecture for our purpose.  

So the input was noise-laden audio STFT slices(to maintain dimensionality of the model) and the output was noise mask STFT of the same dimension as input. When the output is stitched together, we get the noise mask of the input audio, which is nothing but all the noisy frequencies and audio.  

Once we get this noise mask, we then subtract this noise mask from the input audio to get the denoised audio.  
