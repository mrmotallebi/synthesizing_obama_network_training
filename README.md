#README


This is modified research-code for 
[Synthesizing Obama: Learning Lip Sync from Audio.](grail.cs.washington.edu/projects/AudioToObama/)  
Supasorn Suwajanakorn, Steven M. Seitz, Ira Kemelmacher-Shlizerman  
SIGGRAPH 2017

Please see [project website](http://homes.cs.washington.edu/~supasorn/?page=code) for the overview.


Code migrated to run on TensorFlow 1.4 and modified to add inference using sample audio file.


##Basic Intructions:

###Training

To train the network, simply run `python2 run.py --save_dir SAVE_DIR`  
Where `SAVE_DIR` is the directory under ./save/ which the network will be saved. 

###Inference

For inference, the following steps must be taken:

- Install FFMPEG. On Ubuntu it would be `sudo apt-get install ffmpeg`
- Install FFMPEG-Normalize. If you have PIP, you can use `pip install ffmpeg-normalize` , else refer to the [sourcecode page on Github](https://github.com/slhck/ffmpeg-normalize)
- Put your recorded .wav file in the root of the source directory
- Run preprocess.py using `python2 preprocess.py INPUTFILE OUTPUTFILE` where `INPUTFILE` is the input .wav file and `OUTPUTFILE` is the name you want for your output file. (Note: This preprocess is different than the ones used in run.py and util.py)
- Copy the resulting `OUTPUTFILE.npy` to ./obama\_data/audio/normalized-cep13/ 
- Run the inference network using `python2 run.py --save_dir SAVE_DIR --input2 OUTPUTFILE`
- The result should appear in ./results/ directory.

(The above steps can be automated in a script of course.)


##Acknowledgements

This repository is mostly the fork of the [main repository](https://github.com/supasorn/synthesizing_obama_network_training) by the paper's authors.

The MFCC code used is taken from Sphinx3 library.
