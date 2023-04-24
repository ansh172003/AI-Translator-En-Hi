# AI-Translation Tool

The AI-Translation Tool is a Python-based machine translation model that uses the transformers library to translate text from English to Hindi. The model is based on the Helsinki-NLP/opus-mt-en-hi checkpoint.

## Features

- English to Hindi text translation
- Pre-trained model for accurate translations
- Easy to use and integrate into existing Python projects

## Getting Started

To get started with the AI-Translation Tool, you will need to install the following packages:

- transformers
- sentencepiece
- sacremoses
- torch
- torchvision
- torchaudio

You can install these packages using pip, as shown below:

```bash
pip install transformers
pip install sentencepiece
pip install sacremoses
pip install torch torchvision torchaudio
```

After installing the required packages, you can download the pre-trained model and tokenizer using the following code:

```python
from transformers import AutoTokenizer, AutoModelForSeq2SeqLM

tokenizer = AutoTokenizer.from_pretrained("Helsinki-NLP/opus-mt-en-hi")
model = AutoModelForSeq2SeqLM.from_pretrained("Helsinki-NLP/opus-mt-en-hi")

tokenizer.save_pretrained("saved_model/")
model.save_pretrained("saved_model/")
```

This will save the pre-trained model and tokenizer to the "saved_model/" directory on your local machine.

To use the translation tool, you can load the saved tokenizer and model using the following code:

```python
from transformers import AutoTokenizer, AutoModelForSeq2SeqLM

loaded_tokenizer = AutoTokenizer.from_pretrained("saved_model/")
loaded_model = AutoModelForSeq2SeqLM.from_pretrained("saved_model/")
```

You can then define a translation function that takes a text input, encodes it using the loaded tokenizer, generates the translated text using the loaded model, and decodes the output text using the tokenizer. The following code shows an example translation function:

```python
def translator(text):
  input_ids = loaded_tokenizer.encode(text, return_tensors="pt", padding=True)
  outputs = loaded_model.generate(input_ids)
  decoded_text = loaded_tokenizer.decode(outputs[0], skip_special_tokens=True)

  return decoded_text
```

## Usage

To use the translation tool, you can call the "translator" function with an English text input, as shown below:

```python
sentence = input("Enter the sentence : ")
print("Hindi Conversion : ", translator(sentence))
```

This will prompt the user to enter an English sentence, and then print the corresponding Hindi translation.

## Contributing

If you would like to contribute to the AI-Translation Tool, please fork the repository and submit a pull request. We welcome contributions of all kinds, including bug fixes, feature enhancements, and documentation improvements.

Please make sure to update tests as appropriate.

## License

The AI-Translation Tool is licensed under the [MIT](https://choosealicense.com/licenses/mit/) License. See the LICENSE file for more information.
