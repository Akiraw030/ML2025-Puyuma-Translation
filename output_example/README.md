# Output Overview

This folder contains the output files generated after running the whole main.ipynb

## Files

- **nllb-extended**
  Fine-tuned nllb-200-distilled-600M (trained about 45000 steps with loss about 0.0254) (model.safetensors is not pushed due to large file size)

- **all_text_plain.txt**
  The corpus for training new tokenizer, generated from given datasets

- **spm_new.model**
- **spm_new.vocab**
  The trained new tokenizer

- **spm_nllb_extended.model**
  The extended verison of nllb with new tokens

- **submission_NLLB.csv**  
  The inference output of NLLB model, which can score 25.36151

- **submission_FINAL.csv**  
  The inference output of Llama model, which can score 11.41085