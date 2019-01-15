# homebrew-myn

Brew formulae I need, that are not part of homebrew-core

## How to install Python 3.6.8 on macOS Mojave

```bash
brew tap myukselen/myn
brew install python@3.6
python3.6 --version
```

# Starting points

I just wanted to install tensorflow-gpu. Bleeding edge homebrew gives you python 3.7 as default.

Now I have python3.6, lets find out tensorflow-gpu will be happy.

New virtual environment for python 3.6

```bash
mkvirtualenv --python=python3.6 phd36
python --version
pip --version
```

Sounds good. Lets install tensorflow-gpu

```bash
workon phd36
pip install tensorflow-gpu
```

Now you have old one (tensorflow-gpu 1.1) while you can have more up to date (tensorflow 1.12).

After trying to follow https://www.tensorflow.org/install/source and reading a lot of issues on macOS, I was doubting the effort I put in this endavour. 

Seeing someone losing %30 performance was the last nail in the coffin. https://github.com/zylo117/tensorflow-gpu-macosx/issues/1

Back to CPU only.

```bash
workon phd36
pip uninstall tensorflow
pip install tensorflow
python /usr/local/Homebrew/Library/Taps/myukselen/homebrew-myn/test/test-tensorflow.py
```



# Troubleshootings

## Python SSL

When you receive this error on your first pip, don't quit.
"pip is configured with locations that require TLS/SSL, however the ssl module in Python is not available."

Homebrew have a gentle touch on setup.py in python@2 formula, so added ssl library search. Looking at 'brew --prefix openssl' rather than /usr/local/ssl

