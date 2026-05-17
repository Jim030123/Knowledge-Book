
```
pip install llama-stack
```


How to download the model

Visit the [Llama repository](https://github.com/meta-llama) in GitHub where instructions can be found in the [Llama README](https://github.com/meta-llama/llama-models?tab=readme-ov-file#download).

1

Install the Llama CLI

In your preferred environment run the command below:

Command

Use -U option to update llama-stack if a previous version is already installed:

Command

2

Find models list

See latest available models by running the following command and determine the model ID you wish to download:

Command

If you want older versions of models, run the command below to show all the available Llama models:

Command

3

Select a model

Select a desired model by running:

Command

4

Specify custom URL

Llama 3.2: 1B & 3B

When the script asks for your unique custom URL, please paste the URL below

URL

Please save copies of the unique custom URLs provided above, they will remain valid for **48 hours to download each model up to 5 times**, and requests can be submitted multiple times. An email with the download instructions will also be sent to the email address you used to request the models.

  

Available models

With each model size, please find:

1. Pretrained weights: These are base weights that can be fine-tuned, domain adapted with full flexibility.
2. Instruct weights: These weights are for the models that have been fine-tuned and aligned to follow instructions. They can be used as-is in chat applications or futher fine tuned and aligned for specific use cases.
3. Protections model: We offer specialized models tailored specifically to developers' needs to detect and filter problematic content or policy-violating inputs and outputs in text and images.

Available models for download include:

- Pretrained:
- - Llama-3.2-1B
    - Llama-3.2-3B
- Fine-tuned:
- - Llama-3.2-1B-Instruct
    - Llama-3.2-1B-Instruct-QLORA_INT4_EO8
    - Llama-3.2-1B-Instruct-SpinQuant_INT4_EO8
    - Llama-3.2-3B-Instruct
    - Llama-3.2-3B-Instruct-QLORA_INT4_EO8
    - Llama-3.2-3B-Instruct-SpinQuant_INT4_EO8
- Protections models:
- - Llama-Guard-3-1B
    - Llama-Guard-3-1B-INT4