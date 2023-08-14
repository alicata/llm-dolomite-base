# llm-dolomite-base: fine-tuning
Baselines for fine-tuning common LLM models ([Falcon-7b](https://huggingface.co/tiiuae/falcon-7b), LLama2)

# GPU: A100 40GB VRAM 
|  model    | pre-trained weights | fine-tuning method / dataset | fine-turning duration, iters | train/val loss | test acc | patch scripts & notebook |  
| ------------ | ------------ | ------------ | ------------ | ------------ | ------------ | ------------ |  
| falcon-7b   | tiiuae, RefinedWeb 1.5B tokens  | Lora, alpaca 52k instruction | 117 min, 50k | 3.6/8.8 *BUG?* | ~ | finetune_falcon-7b_A100_40GB.ipynb |
| falcon-7b   | tiiuae, RefinedWeb 1.5B tokens  | Lora, alpaca 52k instruction | 117 min, 100k | 3.3/~8 *BUG?* | ~ | finetune_falcon-7b_A100_40GB.ipynb |
| *falcon-7b*   | tiiuae, RefinedWeb 1.5B tokens  | adapter_v2, alpaca 52k instruction | 110 min, 35k | *0.5/15.8* | ~ | finetune_falcon-7b_A100_40GB_baselines.ipynb |

### Best Baseline
Falcon-7b + Adapter_V2 + Alpaca performance as expected even after few iterations loss < 1.0. Lora version seems buggy, train loss ~3 even after 100k iterations.

### TODO
* packaing: covert pth model to original format
* validation: inference test/comparison of original and fine-tuned against Alpaca examples
* run eval scripts to generate metrics
* hoock metrics to weights and biases

## Falcon Steps
The main script is <b>[finetune_falcon-7b_lora_A100_40GB](https://github.com/alicata/llm-dolomite-base/blob/main/finetune_falcon-7b_A100-40GB.ipynb)</b>. The script setups lit-gpt repo, installs dependencies, downloads weights+data downloaded.

* [Launch](https://colab.research.google.com/drive/1nSmYyh4k-JfKmO-UuABLA2NZrLdpfBnu) an A100-40GB GPU run-time
* Run script [finetune_falcon-7b_lora_A100_40GB](https://github.com/alicata/llm-dolomite-base/blob/main/finetune_falcon-7b_A100-40GB.ipynb)
* Patch the [lit-gpt/finetune](https://github.com/Lightning-AI/lit-gpt/tree/main/finetune) folder with lora_compact.py (resolves A100-40GB memory conflicts)
* Start finetuning training (50k iteration)
* At completion compare the losses/accuracy/quality with corresponding the expect_tune folder or the summary table above

### Downloaded Falcon-7b Weights and Dataset 
![pretrained](https://github.com/alicata/llm-dolomite-base/blob/main/fs_pretrained_checkpoints_dataset.png)

## Convert Finetuned Model back to Original Weights Format
After finetuning with LoRA, covert the finetuned model output/lit_model_lora_finetuned.pth back to its original weights naming convention. 

Use --checkpoint_name:
```
python scripts/convert_lit_checkpoint.py \
    --checkpoint_name lit_model_lora_finetuned.pth \
    --checkpoint_dir checkpoints/tiiuae/falcon-7b
``` 

# Experiments Build Setups
| build setup   | Cons | Pros | 
| ------------ | ------------ |  ------------ | 
| finetune_falcon-7b_A100-40GB.ipynb, lit-gpt, lora.py patch  | need to patch checked out repo with lora_compact.py  | sync easily with lit-gpt |
| finetune_falcon-7b_A100-40GB.ipynb, forked lit-gpt | fork can get out-of-sync | no patch, single setup step with notebook |
| finetune_falcon-7b_A100-40GB_mods.ipynb | needs 1-time testing for customization of lora.py  | single step script, best for testing setup on Lambda/Colab |



## Mods
Most src files are mods of [lit-gpt](https://github.com/Lightning-AI/lit-gpt) code to make reproducibility more consistent and easier, however the baselines should work also with bare pytorch train code

# Exploartory Data Analysis
* [Alpaca dataset](https://github.com/alicata/llm-dolomite-base/blob/main/tuning_data/dataset_alpaca.md)
* [RefineWeb](https://github.com/alicata/llm-dolomite-base/blob/main/tuning_data/dataset_refineweb.md)
* [CommonCrawl](https://github.com/alicata/llm-dolomite-base/blob/main/tuning_data/dataset_commoncrawl.md)
  


