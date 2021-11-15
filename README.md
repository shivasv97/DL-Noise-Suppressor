# DL-Noise-Suppressor

### Details

This solution is to tackle the problem of noise entering the mic of the speaker causing issues in audio making it hard to hear the speaker. This solution aims to suppress the noise being broadcasted onto the meeting by using deep learning.  


Using Deep learning, we can remove some of the unwanted bundles of frequencies by representing the audio files as STFTs or Short Term Fourier Transform. This input format can be represented as an image which are posted below.  

The architecture which is being used for this solution is the UNet model which was originally designed for edge detection tasks in medical imaging. Since spectrograms are also a form of an image, we can utilise this architecture for our purpose.  

So the input was noise-laden audio STFT slices(to maintain dimensionality of the model) and the output was noise mask STFT of the same dimension as input. When the output is stitched together, we get the noise mask of the input audio, which is nothing but all the noisy frequencies and audio.  

Once we get this noise mask, we then subtract this noise mask from the input audio to get the denoised audio.  

### Further Improvements

Currently this POC model is trained on a meagre 1.8k training samples of a little over 1 second each. This was due to lack of compute and memory resources available for training this huge model and the dataset.   
The total dataset consists of 3hrs of voice mixed in noise audio clips. This POC model can remove upto 60-70% of the noise present in a new audio sample which the model has not seen.    

The next steps would be to increase the dataset size and distribution such as including more types of noise samples and more speaker voices. This would significantly improve the amount of noise supression being done, to upto 80 or even 90%.  
Also transfer learning for UNet could be tried out as well, where the pretrained UNet model is fine-tuned upon this Audio dataset to improve performance.  

Once we achieve a good level of noise suppression, we could add onto this concept and try to filter out only the speaker's voice using voice recognition. This would then mean that speaker can still have good clarity on the call even they were taking the call in a busy coffeeshop, for instance.  
