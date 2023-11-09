[suno/bark-small · Hugging Face](https://huggingface.co/suno/bark-small)

> You can run Bark locally with the 🤗 Transformers library from version 4.31.0 onwards.

1.  First install the 🤗 [Transformers library](https://github.com/huggingface/transformers) and scipy:

````
```pip install --upgrade pip
     pip install --upgrade transformers scipy
```

 2.  Run inference via the `Text-to-Speech` (TTS) pipeline. You can infer the bark model via the TTS pipeline in just a few lines of code!
>
     from transformers import pipeline
     import scipy

     synthesiser = pipeline("text-to-speech", "suno/bark-small")

     speech = synthesiser("Hello, my dog is cooler than you!", forward_params={"do_sample": True})

     scipy.io.wavfile.write("bark_out.wav", rate=speech["sampling_rate"], data=speech["audio"])


 3.  Run inference via the Transformers modelling code. You can use the processor + generate code to convert text into a mono 24 kHz speech waveform for more fine-grained control.

     from transformers import AutoProcessor, AutoModel

     processor = AutoProcessor.from_pretrained("suno/bark-small")
     model = AutoModel.from_pretrained("suno/bark-small")

     inputs = processor(
         text=["Hello, my name is Suno. And, uh — and I like pizza. [laughs] But I also have other interests such as playing tic tac toe."],
         return_tensors="pt",
     )

     speech_values = model.generate(**inputs, do_sample=True)


 4.  Listen to the speech samples either in an ipynb notebook:

     from IPython.display import Audio

     sampling_rate = model.generation_config.sample_rate
     Audio(speech_values.cpu().numpy().squeeze(), rate=sampling_rate)


 Or save them as a `.wav` file using a third-party library, e.g. `scipy`:

     import scipy

     sampling_rate = model.config.sample_rate
     scipy.io.wavfile.write("bark_out.wav", rate=sampling_rate, data=speech_values.cpu().numpy().squeeze())
>
>
> For more details on using the Bark model for inference using the 🤗 Transformers library, refer to the [Bark docs](https://huggingface.co/docs/transformers/model_doc/bark).
>
> ## Suno Usage
>
> You can also run Bark locally through the original [Bark library](https://huggingface.co/suno/bark-small/blob/main/(https://github.com/suno-ai/bark):
>
> 1.  First install the [`bark` library](https://github.com/suno-ai/bark)
>
> 2.  Run the following Python code:
>
>
>     from bark import SAMPLE_RATE, generate_audio, preload_models
>     from IPython.display import Audio
>
>     # download and load all models
>     preload_models()
>
>     # generate audio from text
>     text_prompt = """
>          Hello, my name is Suno. And, uh — and I like pizza. [laughs]
>          But I also have other interests such as playing tic tac toe.
>     """
>     speech_array = generate_audio(text_prompt)
>
>     # play text in notebook
>     Audio(speech_array, rate=SAMPLE_RATE)
>
>
> [pizza.webm](https://user-images.githubusercontent.com/5068315/230490503-417e688d-5115-4eee-9550-b46a2b465ee3.webm)
>
> To save `audio_array` as a WAV file:
>
>     from scipy.io.wavfile import write as write_wav
>
>     write_wav("/path/to/audio.wav", SAMPLE_RATE, audio_array)
````
