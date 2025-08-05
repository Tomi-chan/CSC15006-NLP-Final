# Preprocess data and create new tokenizer

This is our project for Natural Language Processing with subject: Building SinoNomBert based on Bert Ancient Chinese

## Installation

Use the package manager [pip](https://pip.pypa.io/en/stable/) to install these libraries.

```bash
pip install transformers==4.47.0
pip install pandas==2.2.3
```
### Note: Different versions of the transformers library may not run BertTokenizer correctly in add_tokens.ipynb.
## Usage
- Folder `Data`: Contains raw SinoNom data from chunom.org, nomfoundation.org, etc.
- Folder `ProcessedData`: Contains cleaned data after processing in combined.ipynb.
- Folder `Vocab`: Contains all files that include any characters from SinoNom documents.
- Folder `Tokenizer`,`NomBertTokenizer`, `NomBertAutoTokenizer` : Contain saved tokenizers. NomBertTokenizer is the preferred tokenizer for use in this project.

The combined.ipynb file is a Jupyter Notebook outlining a comprehensive workflow for data preprocessing and vocabulary creation. This document explains the steps involved, making it easier for users to understand and replicate the process.

Additionally, this repository contains two other notebooks:

add_tokens.ipynb: This is the working version of the tokenizer we have and can implement into our project.
add_tokens_fast.ipynb: This file is for testing with AutoTokenizer, which includes a tokenizer.json file. (Note: we have not been able to use this version yet.)

## Contributing

Pull requests are welcome. For major changes, please open an issue first
to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License

[MIT](https://choosealicense.com/licenses/mit/)
