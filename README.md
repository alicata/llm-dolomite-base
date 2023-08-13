# llm-dolomite-base: fine-tuning
Baselines for fine-tuning common LLM models (Falcon-7b, LLama2)

# GPU: A100 40GB VRAM 
|  model    | pre-trained weights | fine-tuning method / dataset | fine-turning duration, iters | train/val loss | test acc | patch scripts & notebook |  
| ------------ | ------------ | ------------ | ------------ | ------------ | ------------ | ------------ |  
| falcon-7b   | tiiuae, RefinedWeb 1.5B tokens  | Lora, alpaca 52k instruction | 117 min, 50k | 3.6/8.8 | ~ | finetune_falcon-7b_lora_A100_40GB.ipynb |


