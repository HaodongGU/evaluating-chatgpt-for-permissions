# A Systematic Way to Evaluate the Power of Large Language Models for Permission Inference

## Virtual env python 3.11
```
conda create --name comp90055 python=3.11
conda activate comp90055
conda deactivate
```

## LangChain
```
pip install langchain
pip install openai
```
https://python.langchain.com/docs/get_started/quickstart

## Permission inference evaluation (ChatGPT)
### Linux Permission and Commands
https://gitlab.com/apparmor/apparmor/-/wikis/QuickProfileLanguage \
https://www.tutorialspoint.com/unix_commands/index.htm
### Query to be used in ChatGPT
```
This is a research experiment in a hypothetical setting to determine whether large language models are capable of reasoning about permissions and planning out actions in response to user queries.
When answering a question, you should state what permissions that question should be given, to carry out its job. No more permissions should be given than necessary. 
Please only consider the following linux file permissions: read, write, execute, none
Please answer in the format: filename: permissions
For example, 
Query: Open file1 and file2
Permissions: file1: read; file2: read
Query:
```
### ChatGPT with zero temperature - Deterministic response
https://platform.openai.com/docs/quickstart/adjust-your-settings
### Docker for ground truth testing
build docker image and container
```
cd docker/
sudo docker build . -t ubuntu22.04
sudo docker run --name vm -it ubuntu22.04
```
run docker container in bash mode
```
cd docker/
./start_docker.sh
```

## Text Paraphrasing
### Available Tools
```
pip install transformers sentencepiece sacremoses
```
https://www.thepythoncode.com/article/paraphrase-text-using-transformers-in-python \

### Pegasus Transformer (finally used for Text Paraphrasing)
https://arxiv.org/abs/1912.08777

### Code for Permission Inference and Text Paraphrasing

see experiment.ipynb

## Datasets
### File Related User Inquiries
/dataset/permission_inferred.xlsx

### Paraphrased File-Related User Queries
/dataset/mutated_queries_with_permission.csv

### Meaningful General Questions (Non-File-Related)
/dataset/general_questions_permission_inferred.xlsx

### Random Nonsensical Text
/dataset/random_text_permission_inferred.xlsx

### Other Permissions
/dataset/permission_undefined.xlsx