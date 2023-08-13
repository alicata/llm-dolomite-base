# llm-dolomite-base: LLM fine-tuning 
Baselines for fine-tuning common LLM models (Falcon-7b, LLama2)

# GPU: A100 40GB VRAM
|  model    | pre-trained weights | pre-trained dataset | fine-tuning method | fine-tuning dataset | fine-turning duration | train loss | val loss | eval accuracy | script | notebook |
| ------------ | ------------ | ------------ | ------------ | ------------ | ------------ | ------------ | ------------ | ------------ | ------------ | ------------ | 
| falcon-7b   | tiiuae url | RefinedWeb 1.5B tokens  | Lora |  alpaca 52k instruction (synth) | 117 min / 50k iters | 3.6 | 8.8 | ~ | finetune/lora_compact.py / tune_A100_40GB.sh | falcon_finetune_lora.jynp |


