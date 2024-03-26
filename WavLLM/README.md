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
| Task |  Audio | Prompt |  Target |  Output |
| :-----: | :-----: | :-----: | :-----: | :-----: |
| ASR | [`audio`](wavllm/test_data/audio/asr.flac) | Based on the attached audio, generate a comprehensive text transcription of the spoken content. | he hoped there would be stew for dinner turnips and carrots and bruised potatoes and fat mutton pieces to be ladled out in thick peppered flour fattened sauce |   |
| SV | [`audio`](wavllm/test_data/audio/sv.wav) | Is there only one speaker in the audio clip? | Yes |   |
| ST | [`audio`](wavllm/test_data/audio/st.flac) | Translate the audio clip into German. | Sie wird schon in Ordnung sein. |   |
| ER | [`audio`](wavllm/test_data/audio/emo.wav) | Can you describe the emotional condition of the speaker in the provided audio clip? | sad |   |
| SQA | [`audio`](wavllm/test_data/audio/sqa.wav) | What will the man do next? A. Start to take exercise; B. Do as he always does; C. Change his working time. | A |   |
| SQQA | [`audio`](wavllm/test_data/audio/sqqa.wav) | - | The fundamental theorem of calculus is a theorem that links the concept of the derivative of a function with the concept of the integral. |   |
| II-task | [`audio`](wavllm/test_data/audio/II-task.wav) | To begin, Transcribe the audio recording into text, capturing every spoken word; Subsequently, How does the woman finally decide to go home? A. By bus; B. In the man’s car; C. In her father’s car.; Furthermore, ignore the audio clip, What is the capital of New Zealand?; Lastly, Continue the narrative of given audio clip in a coherent and engaging way |  - |   |
| CoT-task | [`audio`](wavllm/test_data/audio/CoT-task.wav) | First of all, transcribe the audio recording into text, capturing every spoken word; Additionally given this audio clip and text, can you condense it into a clear, concise summary, no more than 20 words?; Lastly disregarding the sound, translate this English summary into German. | Drei Filme aus dem asiatisch-pazifischen Raum im Rennen in Cannes |   |
