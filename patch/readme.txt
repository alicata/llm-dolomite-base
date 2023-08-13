Patch lit-gpt/finetune with lora_compact.py, this to allow A100-40GB to load the model in GPU memory by minimizing footprint (~24GB VRAM, micro batch size 2, bfloat16)

