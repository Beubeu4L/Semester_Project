## Data Set Generator for NN Training
Generate 256x256 patches with synthetic streaks in it. 

`python new_synthetic_generator.py --i "your_image_path.fits" --o "label" --n 2`

* --i : the patches will be generated from this original fits image;
* --o : the generator will generate three .npy file, the first one corresponds to the features, the others are the targets. The name of this files will be named after this argument. 
With the example above, the files will be named "label_samples.npy", "label_targets.npy", "label_patch_targets.npy";
* --n : the number of samples we want to generate with a single 64x64 block from the original image. 
The files will be saved in the trainset folder. To run this file, one need to import a .fits image, which was too heavy to be put on the github.

## Generating the data for the GAN 
`python creating_data_Gan.py`
It calls without argument.
It loads the data generated by new_synthetic_generator.py and separates it into a set X (RGB image) containing the satellite streaks, and a set Y 
(RGB image) which doesn't contain satelitte streaks.

## Training the GAN
`python Gan.py`
It calls without argument.
It loads the X and Y sets and traing the GAN, which is implemented following : https://github.com/junyanz/pytorch-CycleGAN-and-pix2pix
The results are saved into the checkpoint folder. It need to be run on a server (because it is computationnally expensive
, which a batch file such as GAN.bat). You can modifiy directly the hyper-parameters of the model in the file.