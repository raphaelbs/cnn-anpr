# Deep ANPR

Using neural networks to build an automatic number plate recognition system.
See [this blog post](http://matthewearl.github.io/2016/05/06/cnn-anpr/) for an
explanation.

**Note: This is an experimental project and is incomplete in a number of ways,
if you're looking for a practical number plate recognition system this project
is not for you.**

# Requirements

This project relies on `Python 3.6 x64` if you are using Windows.

Has the following dependencies:

* numpy==1.15.4
* opencv_python==3.4.4.19
* matplotlib==2.0.2
* Pillow==5.3.0
* tensorflow==1.12.0

Different typefaces can be put in `fonts/` in order to match different type
faces. With a large enough variety the network will learn to generalize and
will match as yet unseen typefaces. See
[#1](https://github.com/matthewearl/deep-anpr/issues/1) for more information.

You can install all required packages using:

> pip install -r ./requirements.txt

# Usage

1. `./extractbgs.py SUN397.tar.gz`: Extract ~3GB of background images from the [SUN database](http://groups.csail.mit.edu/vision/SUN/)
   into `bgs/`. (`bgs/` must not already exist.) The tar file (36GB) can be [downloaded here](http://vision.princeton.edu/projects/2010/SUN/SUN397.tar.gz).
   This step may take a while as it will extract 108,634 images.

2. `./gen.py 1000`: Generate 1000 test set images in `test/`. (`test/` must not
    already exist.) This step requires some font in the
    `fonts/` directory. You can download the UK version
    [here](http://www.dafont.com/uk-number-plate.font).

3. `./train.py`: Train the model. A GPU is recommended for this step. It will
   take around 100,000 batches to converge. When you're satisfied that the
   network has learned enough press `Ctrl+C` and the process will write the
   weights to `weights.npz` and return.

4. `./detect.py in.jpg weights.npz out.jpg`: Detect number plates in an image.


