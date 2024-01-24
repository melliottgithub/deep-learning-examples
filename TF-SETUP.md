# Tensorflow with GPU Support on Mac M1/M2

## Install Xcode SDK

```sh
# verify
 xcrun --show-sdk-path

# or install
xcode-select --install
```

## Install Miniconda Python distribution

```sh
brew install --cask miniconda
conda init zsh
```

## Create Conda Environment for Tensorflow

- The package `tensorflow-deps` requires Python 3.10.x

```sh
conda create --name tensorflow python=3.10
```

## Install Tensorflow Depedencies for Apple M1/M2

```sh
conda activate tensorflow
```

- `tensorflow-deps` only works specific version of numpy
```sh
conda install -c cctbx202208 numpy=1.21.6
conda install -c apple tensorflow-deps
```

## Install Tensorflow with Apple plug-in

```sh
pip install tensorflow-metal==1.1.0 tensorflow==2.14
```

## Install additional packages

```sh
pip install -r requirements.txt
```

## Verify Tensorflow devices
```Python
import tensorflow as tf
tf.config.list_physical_devices()
```

```txt
[PhysicalDevice(name='/physical_device:CPU:0', device_type='CPU'),
 PhysicalDevice(name='/physical_device:GPU:0', device_type='GPU')]
````

## References
- https://developer.apple.com/metal/tensorflow-plugin/
- https://pypi.org/project/tensorflow-metal/