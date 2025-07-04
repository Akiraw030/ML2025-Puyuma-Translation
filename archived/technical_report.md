# ML2025 Bonus Competition Puyuma translation technical report

## Team Akiraw03030

- OOO

## Model used

1. facebook/nllb-200-distilled-1.3B. [Huggingface](https://huggingface.co/facebook/nllb-200-distilled-1.3B)
2. facebook/nllb-200-distilled-600M. [Huggingface](https://huggingface.co/facebook/nllb-200-distilled-600M)
3. meta-llama/Llama-3.2-3B-Instruct. [Huggingface](https://huggingface.co/meta-llama/Llama-3.2-3B-Instruct)

## Methods

1. Using the given dataset to train a new tokenizer by SentencePieceTrainer, and then add the missing tokens into model and tokenizer. (Original NLLb tokenizer would have many Chinese characters missing(tokenize into unk), which is a reported issue on github. [Link](https://github.com/facebookresearch/fairseq/issues/4560))
2. Using Adafactor optimizer and given dataset to finetune NLLB model for puyuma translation. Then, use the finetuned model to generate answer.
3. Like the method of HW1, using two prompted LLM agents to get the final results, each for one direction of translating. The agents are fed with several datas for reference, including the translated answer from NLLB model, related translated pair from given dataset (done by some simple data seletion), content of grammar book from hint of this competition (manually feed the 3rd chapter of the grammar book into Gemini to generate a concentrated version of context). 

## Citation

1. NLLB github repository. [Github](https://github.com/facebookresearch/fairseq/tree/nllb)
2. NLLB homepage. [Meta](https://ai.meta.com/research/no-language-left-behind/)
3. Flores-200 language code. [Github](https://github.com/facebookresearch/flores/tree/main/flores200)
4. Huggingface translation introduction. [Huggingface](https://huggingface.co/docs/transformers/main/en/tasks/translation)
5. Huggingface NLLB introduction. [Huggingface](https://huggingface.co/docs/transformers/main/en/model_doc/nllb)
6. How to fine-tune a NLLB-200 model for translating a new language. [Medium](https://cointegrated.medium.com/how-to-fine-tune-a-nllb-200-model-for-translating-a-new-language-a37fc706b865)
7. ML2025 HW1 sample code. [Kaggle](https://www.kaggle.com/code/u0ulin/ml2025-homework-1)
8. Puyuma grammar. [Taiwanese Indigenous Ebooks](https://alilin.cip.gov.tw/Book/417)

## Others

- OOO