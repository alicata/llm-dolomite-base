# llm-dolomite-base: fine-tuning
Baselines for fine-tuning common LLM models [Falcon-7b](https://huggingface.co/tiiuae/falcon-7b), LLama2)

# GPU: A100 40GB VRAM 
|  model    | pre-trained weights | fine-tuning method / dataset | fine-turning duration, iters | train/val loss | test acc | patch scripts & notebook |  
| ------------ | ------------ | ------------ | ------------ | ------------ | ------------ | ------------ |  
| falcon-7b   | tiiuae, RefinedWeb 1.5B tokens  | Lora, alpaca 52k instruction | 117 min, 50k | 3.6/8.8 | ~ | finetune_falcon-7b_lora_A100_40GB.ipynb |

## Falcon Steps
The main script is <b>[finetune_falcon-7b_lora_A100_40GB](https://github.com/alicata/llm-dolomite-base/blob/main/finetune_falcon-7b_A100-40GB.ipynb)</b>. The script setups lit-gpt repo, installs dependencies, downloads weights+data downloaded.

* Launch an A100-40GB GPU run-time
* Run script [finetune_falcon-7b_lora_A100_40GB](https://github.com/alicata/llm-dolomite-base/blob/main/finetune_falcon-7b_A100-40GB.ipynb)
* Patch the [lit-gpt/finetune](https://github.com/Lightning-AI/lit-gpt/tree/main/finetune) folder with lora_compact.py (resolves A100-40GB memory conflicts)
* Start finetuning training (50k iteration)
* At completion compare the losses/accuracy/quality with corresponding the expect_tune folder or the summary table above

### Downloaded Falcon-7b Weights and Dataset 
![pretrained](https://github.com/alicata/llm-dolomite-base/blob/main/fs_pretrained_checkpoints_dataset.png)

## Mods
Most src files are mods of [lit-gpt](https://github.com/Lightning-AI/lit-gpt) code to make reproducibility more consistent and easier, however the baselines should work also with bare pytorch train code

