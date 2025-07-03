
# 🧠 Arabic NLP to SQL Converter

This project translates natural language questions written in **Arabic** into executable **SQL queries**. It enables Arabic-speaking users to interact with relational databases using simple Arabic phrases — no SQL knowledge required.

---

## 🚀 Project Overview

While many text-to-SQL systems exist for English, Arabic remains vastly underrepresented. This project bridges that gap by fine-tuning a multilingual transformer model to support SQL generation from Arabic input.

---

## 📚 Dataset

- **Name:** `AR_spider.jsonl`
- **Format:** JSON Lines
- **Fields:**
  - `arabic`: Arabic questions
  - `query`: Ground-truth SQL
  - `table_names`: List of related tables
  - `db_id`: Target database identifier

---

## ⚙️ Methodology

### 1. Preprocessing
- Lemmatization via **Stanza**
- Custom stopword removal
- Table schema injection into prompts

### 2. Prompt Format

```
ترجم إلى SQL: [lemmatized Arabic question] ### الجداول: [table1، table2]
```

### 3. Model
- `google/mt5-small` (Multilingual T5)
- Fine-tuned using **PyTorch** & **Hugging Face Transformers**

### 4. Training
- 8 epochs
- 70/15/15 train/val/test split
- GPU accelerated

### 5. Evaluation Metrics
- ✅ **Exact Match Accuracy**
- ✅ **Execution Accuracy**
- ✅ **BLEU Score**

---

## 🧪 Sample Output

**Arabic Question:**  
ما هي أسماء الأقسام التي يعمل فيها الموظفون؟

**Ground Truth SQL:**  
```sql
SELECT DISTINCT department_name FROM departments JOIN employees ON departments.department_id = employees.department_id;
```

**Predicted SQL:**  
```sql
SELECT DISTINCT department_name FROM departments JOIN employees ON departments.department_id = employees.department_id;
```

✅ Execution Match

---

## 💻 Technologies Used

- Python
- PyTorch
- Hugging Face Transformers
- Stanza (Arabic NLP)
- Jupyter Notebook

---

## 👥 Team Members

- **Youssef Saraya** – 320210002  
- **Omar Samy** – 320210170

---

## 📂 How to Run

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/arabic-nlp-to-sql.git
   cd arabic-nlp-to-sql
   ```

2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. Run the notebook:
   Open `youssefsaraya-nlp.ipynb` in Jupyter and run all cells.

---

## 📄 License

This project is licensed under the **MIT License**.

---

## 🌟 Acknowledgements

Special thanks to open-source contributors of:
- [Hugging Face Transformers](https://huggingface.co/transformers/)
- [Stanza NLP](https://stanfordnlp.github.io/stanza/)
