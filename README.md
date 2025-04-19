# Named Entity Recognition using Hugging Face Transformers

## 📌 Project Overview

This project demonstrates **Named Entity Recognition (NER)** using the [Hugging Face Transformers](https://huggingface.co/transformers/) library. It fine-tunes a pretrained BERT model (`bert-base-uncased`) on the **CoNLL-2003** dataset, which includes entities like persons, organizations, locations, and miscellaneous types.

### Key Highlights
- Uses `bert-base-uncased` for token classification
- Handles token-label alignment using `.word_ids()`
- Fine-tuned using Hugging Face’s `Trainer` API
- Evaluated using the `seqeval` metric

---

## 📂 Dataset

- **Source**: [CoNLL-2003](https://huggingface.co/datasets/conll2003)
- **Access**: Automatically downloaded using `datasets.load_dataset('conll2003')`
- **Entity Types**: `PER`, `ORG`, `LOC`, `MISC`
- **Structure**: Token-level annotations for named entities

---

## 🛠 Installation

Install all required dependencies with:

```bash
pip install transformers datasets tokenizer seqeval evaluate accelerate
```

---

## 🧠 Model and Tokenization

- **Tokenizer**: `BertTokenizerFast` from `bert-base-uncased`
- Tokenization with `is_split_into_words=True` for word-level alignment
- Labels are aligned to subword tokens using a custom function:
  ```python
  def tokenize_and_align_label(examples, label_all_tokens=True):
      ...
  ```

---

## 🏋️ Training Configuration

- **Model**: `AutoModelForTokenClassification`  
- **Training Arguments**:
  - Epochs: `10`
  - Learning rate: `2e-5`
  - Batch size: `16` (train & eval)
  - Weight decay: `0.01`
  - Evaluation strategy: `"epoch"`

---

## 📊 Evaluation

- **Metric**: `seqeval` from Hugging Face’s `evaluate` library
- Calculates:
  - Precision
  - Recall
  - F1-score
- Evaluates for each individual entity type (e.g., PER, LOC, ORG)

---

## ✅ Sample Output

Example of token-label alignment:
```
Token: John            Label: B-PER
Token: lives           Label: O
Token: in              Label: O
Token: New             Label: B-LOC
Token: York            Label: I-LOC
```

---

## 📁 File Structure

```bash
NER_using_huggingface_transformer/
├── NER_using_huggingface_transformer.ipynb  # Main notebook
└── README.md                                 # Project documentation
```

---

## 🚀 Future Work

- Upload and deploy model via Hugging Face Model Hub
- Add confusion matrices and per-class evaluation plots
- Explore CRF postprocessing for improved accuracy
- Train on custom NER datasets for domain-specific applications

---

## 🙌 Credits

- 🤗 [Hugging Face](https://huggingface.co/) for `transformers`, `datasets`, `evaluate`
- 🧠 CoNLL-2003 for the NER dataset
- 🔧 Libraries used: `NumPy`, `tokenizers`, `evaluate`, `seqeval`, `transformers`

---

