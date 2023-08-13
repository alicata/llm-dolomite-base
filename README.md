# llm-dolomite-base: fine-tuning
Baselines for fine-tuning common LLM models (Falcon-7b, LLama2)

# GPU: A100 40GB VRAM 
|  model    | pre-trained weights | fine-tuning method / dataset | fine-turning duration, iters, cost* | train/val loss | eval accuracy | script | notebook |  
| ------------ | ------------ | ------------ | ------------ | ------------ | ------------ | ------------ | ------------ | 
| falcon-7b   | tiiuae / RefinedWeb 1.5B tokens  | Lora, alpaca 52k instruction | 117 min, 50k,   $2-$4 | 3.6/8.8 | ~ | finetune/lora_compact.py   tune_A100_40GB.sh | falcon_finetune_lora.jynp |
* cost based on Lambda server, ColabPro

