# Puyuma Translation Bonus Competition Project

### Competition webpage: [Kaggle](https://www.kaggle.com/competitions/ml-2025-bonus-competition/overview)

This project is an entry for the ML2025 Spring Puyuma translation bonus competition on Kaggle.

## Environment

- **Platform:** Kaggle
- **Accelerators:** T4*2

## How to run

To run this project, upload the main.ipynb notebook to Kaggle along with the provided datasets. Ensure you configure the Kaggle environment with appropriate GPU settings.

## Others

- **NLLB Fine-tuning (PART2):** The fine-tuning process for the NLLB model may take up to 12 hours, which is the time limit of Kaggle.
- **Archived Versions:** For the main.ipynb notebook and the technical report of the version when the last submission is made, please see archived.

## Data Source

This repository includes data derived from **FormosanBank**, subject to the following terms:

- **No Commercial AI Use**: This dataset or any derivative works may not be used, in whole or in part, for the development, training, testing, or deployment of artificial intelligence systems intended for commercial purposes.
- **License**: The annotations and metadata are licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). Attribution is required for any redistribution or derived products.

### Source Attribution

> FormosanBank. [https://github.com/formosanbank/formosanbank](https://github.com/formosanbank/formosanbank)

###

# Project Details

## Model used 

1. facebook/nllb-200-distilled-600M. [Huggingface](https://huggingface.co/facebook/nllb-200-distilled-600M)
1. meta-llama/Llama-3.2-3B-Instruct. [Huggingface](https://huggingface.co/meta-llama/Llama-3.2-3B-Instruct)

## Methods

1. Using the given dataset to train a new tokenizer by SentencePieceTrainer, and then add the missing tokens into model and tokenizer. (Original NLLb tokenizer would have many Chinese characters missing(tokenize into unk), which is a reported issue on github. [Link](https://github.com/facebookresearch/fairseq/issues/4560))
2. Using Adafactor optimizer and given dataset to finetune NLLB model for puyuma translation. Then, use the finetuned model to generate answer.
3. Like the method of HW1, using two prompted LLM agents to get the final results, each for one direction of translating. The agents are fed with several datas for reference, including the translated answer from NLLB model, related translated pair from given dataset (done by some simple data seletion), content of grammar book from hint of this competition (manually feed the 3rd chapter of the grammar book into Gemini to generate a concentrated version of context). 

## Citation & References

1. NLLB github repository. [Github](https://github.com/facebookresearch/fairseq/tree/nllb)
2. NLLB homepage. [Meta](https://ai.meta.com/research/no-language-left-behind/)
3. Flores-200 language code. [Github](https://github.com/facebookresearch/flores/tree/main/flores200)
3. Sentencepiece github repository. [Github](https://github.com/google/sentencepiece)
4. Huggingface translation introduction. [Huggingface](https://huggingface.co/docs/transformers/main/en/tasks/translation)
5. Huggingface NLLB introduction. [Huggingface](https://huggingface.co/docs/transformers/main/en/model_doc/nllb)
6. How to fine-tune a NLLB-200 model for translating a new language. [Medium](https://cointegrated.medium.com/how-to-fine-tune-a-nllb-200-model-for-translating-a-new-language-a37fc706b865)
7. ML2025 spring HW1 sample code. [Kaggle](https://www.kaggle.com/code/u0ulin/ml2025-homework-1)
8. Puyuma grammar. [Taiwanese Indigenous Ebooks](https://alilin.cip.gov.tw/Book/417)