# How to Run Alpaca locally on a Mac or Linux
https://github.com/ggerganov/llama.cpp

[Habr post (in Russian)](https://habr.com/ru/news/t/723638/) which motivated me to try.

Install `git lfs` (Large File Storage) (see also https://docs.github.com/en/repositories/working-with-files/managing-large-files/installing-git-large-file-storage):
```
brew install git-lfs
git lfs install
```
Create a parent directory for the experiment:
```
mkdir alpaca
```
Download the model weights in ggml format (4bits):
7B version (~4.2Gb file, requires 4.3GB RAM to run):
```
git clone https://huggingface.co/Pi3141/alpaca-7B-ggml
```

30B version (~20GB file, requires 20+GB RAM to run):
```
git clone https://huggingface.co/Pi3141/alpaca-30B-ggml
```

There is also a 13B version available at https://huggingface.co/Pi3141/

Download and build the app:
```
git clone https://github.com/ggerganov/llama.cpp
cd llama.cpp
make
```
Run the model:
```
./chat -m ../alpaca-30B-ggml/ggml-model-q4_0.bin -n 128
```
Enjoy!
