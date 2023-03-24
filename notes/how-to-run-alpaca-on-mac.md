# How to Run Alpaca locally on a Mac or Linux
[Habr post (in Russian)](https://habr.com/ru/news/t/723638/) which motivated me to try this. Check it out for extra references and useful links.

Install `git lfs` (Large File Storage) (see also https://docs.github.com/en/repositories/working-with-files/managing-large-files/installing-git-large-file-storage):
```
brew install git-lfs
git lfs install
```
Create a parent directory for the experiment:
```
mkdir alpaca
cd alpaca
```
Download the model weights in ggml format (4 bits):
- 7B version (~4.2Gb file, requires 4.3GB RAM to run):
```
git clone https://huggingface.co/Pi3141/alpaca-7B-ggml
```
- 30B version (~20GB file, requires 20+GB RAM to run):
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
Run the 7B model in the dialog mode:
```
./chat -m ../alpaca-7B-ggml/ggml-model-q4_0.bin
```
Run the 7B model in the CLI mode with the prompt="Tell me about alpacas":
```
./chat -m ../alpaca-7B-ggml/ggml-model-q4_0.bin -p "Tell me about alpacas"
```
Replace `alpaca-7B-ggml` with `alpaca-30B-ggml` to run the 30B model. The inference is way slower, though.

Get help on available parameters:
```
./chat -h
```
Enjoy!
