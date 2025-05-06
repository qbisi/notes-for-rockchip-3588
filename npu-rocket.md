# Rocket NPU Driver

Collabora's RK3588-specific images include the work-in-progress "Rocket" driver 
in both kernel and Mesa to make use of the NPU. This driver is based on mainline 
sources, and the eventual goal is to have it included there. For now, 
Collabora's images ship it so that users can experiment with it.

The driver consists of a kernel driver, built on the new `accel` subsystem in
Linux, and a Teflon delegate in Mesa. The user's NPU workload loads the teflon
delegate with e.g. tflite in the form of a shared library, which then handles
the communication with the kernel side of things through the driver-specific
uAPI while presenting a common interface to the user.


## Installing TFLite Runtime

Unfortunately, Google's tflite-runtime project requires Python <= 3.11, whereas 
Collabora's images are based on Debian Trixie, which uses Python 3.13.

However, we can use [pyenv](https://github.com/pyenv/pyenv) to grab ourselves
an older Python version.

First, install `pyenv` on your RK3588 board:

    sudo apt update && sudo apt -y install pyenv

We intentionally skip setting up `pyenv`'s shim logic. Next, install Python 3.11
using `pyenv`, run as your user:

    pyenv install 3.11

Please be aware that this will take a few minutes. We can now create a directory
we can use for all of our NPU work, under which `pyenv` will always use
Python 3.11:

    mkdir npu
    cd npu
    pyenv local 3.11

Next, while our current working directory is within that directory, we can 
install TFLite Runtime and the dependencies we need for our example:

    pyenv exec pip install 'numpy<2' tflite-runtime pillow


## Downloading And Running An Example

We can now download a model file, a file with labels for the outputs of the 
model, and an image to test the example script on, as well as the example 
script itself:

    # download and extract the model
    wget http://download.tensorflow.org/models/mobilenet_v1_2018_08_02/mobilenet_v1_1.0_224_quant.tgz
    tar -xf mobilenet_v1_1.0_224_quant.tgz ./mobilenet_v1_1.0_224_quant.tflite
    # get the label data
    wget --content-disposition 'https://gitlab.freedesktop.org/tomeu/mesa/-/raw/rocket/src/gallium/frontends/teflon/tests/labels_mobilenet_quant_v1_224.txt?ref_type=heads&inline=false'
    # get an image to test with
    wget https://upload.wikimedia.org/wikipedia/commons/f/f8/Cat_in_tree03.jpg
    # get the example script
    wget --content-disposition 'https://gitlab.freedesktop.org/tomeu/mesa/-/raw/rocket/src/gallium/frontends/teflon/tests/classification.py?ref_type=heads&inline=false'

You may now run the script as follows, note the delegate being specified with
`-e`:

    pyenv exec python3.11 classification.py -m mobilenet_v1_1.0_224_quant.tflite -l labels_mobilenet_quant_v1_224.txt -i Cat_in_tree03.jpg -e /usr/lib/teflon/libteflon.so

To make sure the delegate is being used, you may specify `TEFLON_DEBUG=verbose`
in your environment to get additional output when running commands such as the
one above that use the teflon delegate. It should show something like
`Teflon delegate: loaded rocket driver` in the first line of verbose output.
