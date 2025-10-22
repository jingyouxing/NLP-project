# NLP-Project

This project uses the **BLEnD: A Benchmark for LLMs on Everyday Knowledge in Diverse Cultures and Languages** (NeurIPS 2024 Datasets and Benchmarks Track) as a baseline to evaluate large language models (LLMs) on culturally grounded, everyday knowledge.
 
Official repository of BLEnD : https://github.com/nlee0212/BLEnD.

The dataset can also be found at [HuggingFace Datasets](https://huggingface.co/datasets/nayeon212/BLEnD).

Currently, the evaluation focuses on the short-answer subset of the Algeria portion of BLEnD.

## Requirements
requirements.txt: new version 

We recommend using Python version $\ge$ 3.10.
```
pip install -r requirements.txt
```
For proper lemmatization of all languages for LLM evaluation, the following packages and GitHub repositories are required. Copy & paste and run the following lines.
```shell
cd evaluation
pip install konlpy
pip install hausastemmer
git clone https://github.com/aznlp-disc/stemmer.git,
cp stemmer/word.txt ./evaluation
cp stemmer/suffix.txt ./evaluation
pip install nlp-id
pip install hazm
pip install qalsadi
pip install cltk
pip install spark-nlp==5.3.3 pyspark==3.3.1
pip install jieba
git clone https://github.com/anoopkunchukuttan/indic_nlp_library.git
git clone https://github.com/anoopkunchukuttan/indic_nlp_resources.git
```

### Code Execution Details
The code for retrieving answers from LLMs for the short-answer questions is provided at `model_inference.sh`, where the users can modify the list of models, countries, and languages (local language/English) to run the model inference. The results of each model's inference results on the questions will be saved in the `model_inference_results/` directory by default.

```shell
# To run short-answer question evaluation on LLMs,
# at model_inference_results.sh, change the following by putting in your own API keys and settings:

export CUDA_VISIBLE_DEVICES=""

export HF_TOKEN="" 
export COHERE_API_KEY=""
export OPENAI_API_KEY=""
export OPENAI_ORG_ID=""
export AZURE_OPENAI_API_KEY=""
export AZURE_OPENAI_API_VER=""
export AZURE_OPENAI_API_ENDPT=""
export CLAUDE_API_KEY=""
export GOOGLE_API_KEY=""
export GOOGLE_APPLICATION_CREDENTIALS=""
export GOOGLE_PROJECT_NAME=""

# Then, run the code below:
$ bash model_inference_results.sh
```
### Our Additions
We implemented eval.py to compute semantic similarity scores between model predictions and human-annotated answers.
