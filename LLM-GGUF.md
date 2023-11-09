# Running inference using GGUF LLM models

There are new options for running AI models using local hardware.  
The new GGUF models are a replacement for the old GGML models used previously.  
This is small example of how you can run interference using these models.

## Inference using ctransformers library

You can run inference with the new GGUF models using the
[ctransformers](https://github.com/marella/ctransformers) library in python.

### Running basic inference

```python
from ctransformers import AutoModelForCasualLM

llm = AutoModelForCasualLM.from_pretrained("/path/to/gguf-model", model_type="llama")

print(llm("I like to code using"))
```

You can also use [huggingface](https://huggingface.co) models directly [^1]

- "marella/gpt-2-ggml"

[^1] When using hugginface GGUF models you must use
model_file="FileNameHere" when creating the instance.

- You can find all the supported supported models and their types
  [here](https://github.com/marella/ctransformers#supported-models)

```python
import gradio as gr
import time
from ctransformers import AutoModelforCasualLM

def load_llm():
  llm = AutoModelForCasualLM.from_pretrained(
    "codellama-13b-instruct.Q4_K_M.gguf",
    model_type= 'llama',
    max_new_tokens 1096,
    repetition_penality 1.13,
    temperature = 0.1,
  )
  return llm

def llm_function(message, chat_history):
  llm = load_llm()
  response = llm(
    message
  )
  output_texts = response
  return ooutput_texts


title = "Codellama 13B GGUF Demo"

examples = [
  "Write a python code to connect with a SQL database and list down all the tables.",
  "Write the python code to train a linear regression model using scikit learn.",
  "Write code to implement a binary tree implementation in C language.",
  "What are the benefits of the python programming language?"

]

gr.ChatInterface(
  fn = llm_function,
  title = title,
  examples = examples
)

```
