# llm-dolomite-base: fine-tuning
Baselines for fine-tuning common LLM models (Falcon-7b, LLama2)

# GPU: A100 40GB VRAM 
|  model    | pre-trained weights | fine-tuning method / dataset | fine-turning duration, iters | train/val loss | test acc | patch scripts & notebook |  
| ------------ | ------------ | ------------ | ------------ | ------------ | ------------ | ------------ |  
| falcon-7b   | tiiuae, RefinedWeb 1.5B tokens  | Lora, alpaca 52k instruction | 117 min, 50k | 3.6/8.8 | ~ | finetune_falcon-7b_lora_A100_40GB.ipynb |

## Steps
* Spin up an A100-40GB run-time and run the finetune_falcon-7b_lora_A100_40GB script
* The script setups lit-gpt repo, installs dependencies, downloads weights+data downloaded
* Patch the lit-gpt/finetune/ folder with A100-40GB friendly lora_compact.py
* Start finetuning training (50k iteration)
* At completion compare the losses/accuracy/quality with corresponding the expect_tune folder or the summary table above

## Downloaded Weights and Dataset 
![pretrained](https://github.com/alicata/llm-dolomite-base/blob/main/fs_pretrained_checkpoints_dataset.png)
