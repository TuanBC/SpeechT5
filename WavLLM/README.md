# WavLLM

## Model
| Model |  Model_path |
| :-----: | :-----: |
| WavLLM | [Azure Storage](https://valle.blob.core.windows.net/share/wavllm/final.pt?sv=2021-10-04&st=2024-03-22T11%3A04%3A00Z&se=2025-05-23T11%3A04%3A00Z&sr=b&sp=r&sig=K77BMU5ZMqGnwYrTUsVI26fFQB53rneekGplm4liZ8M%3D)|


## Setup

```bash
git submodule update --init WavLLM/fairseq
cd WavLLM/
conda create -n wavllm python=3.10.0
conda activate wavllm
pip install --editable fairseq/
pip install sentencepiece
pip install transformers==4.32.1
pip install numpy==1.23.5
pip install editdistance
pip install soundfile
```

## Inference
```bash
cp -r wavllm fairseq/examples
cd fairseq
bash examples/wavllm/scripts/inference_sft.sh $model_path $data_name
```
We provided examples of each task in [`test_data`](wavllm/test_data)

## Examples
| Task |  Audio |  Transcript | Prompt |  Output |
| :-----: | :-----: | :-----: | :-----: | :-----: |
| ASR | [`audio`](wavllm/test_data) | [`audio`](wavllm/test_data) | [`audio`](wavllm/test_data) | [`audio`](wavllm/test_data) |
