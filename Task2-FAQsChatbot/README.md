# FAQ Chatbot with Flask

A lightweight, local e-commerce FAQ chatbot built using Natural Language Processing (NLP) and a Flask web interface. The chatbot matches user inquiries against an FAQ dataset using **TF-IDF text vectorization** and **Cosine Similarity** to serve accurate answers instantly.

## 🚀 Features

* **Text Preprocessing:** Tokenization, lowercase conversion, stop-word removal, and lemmatization powered by `nltk`.
* **Vector Search:** Employs `scikit-learn`'s `TfidfVectorizer` and `cosine_similarity` to mathematically find the closest matching question in the dataset.
* **Web Interface:** A clean, responsive chat UI built with HTML/CSS and vanilla JavaScript.
* **Asynchronous Backend:** A Python Flask API endpoint (`/chat`) that handles requests asynchronously without reloading the page.

---

## 🛠️ Prerequisites & Installation

Make sure you have Python installed, then follow these steps:

1. **Clone the repository and navigate to the project directory:**
```bash
git clone https://github.com/BasselAtef/codealpha_tasks.git
cd Task2-FAQsChatbot
run `python faqschatbot.py`

```


2. **Install the required dependencies:**
```bash
pip install pandas numpy nltk scikit-learn flask

```


3. **Prepare the dataset:**
Ensure you have your FAQ dataset named `Ecommerce_FAQs.csv` placed in the root directory. The CSV file must contain at least two columns: `prompt` and `response`.

---

## 💻 How to Run

1. **Execute the Python script:**
```bash
python faqschatbot.py

```


*Note: On the first run, the script will automatically download the necessary NLTK data packets (`punkt`, `wordnet`, `stopwords`, and `punkt_tab`).*
2. **Open the App:**
Once the Flask server boots up, open your web browser and navigate to:
```text
http://127.0.0.1:5000/

```



---

## 📂 Project Structure

```text
├── Ecommerce_FAQs.csv     # FAQ dataset (User Prompts & Responses)
├── faqschatbot.py         # Main application script (Data processing, Logic & Flask Server)
└── templates/
    └── index.html         # Auto-generated chat UI template

```

---

## 🔍 How it Works

1. **Data Ingestion:** Loads `Ecommerce_FAQs.csv` into a Pandas DataFrame.
2. **NLP Cleaning:** The `preprocess_text` function strips punctuation, converts characters to lowercase, drops common stop-words, and lemmatizes words to their base form.
3. **TF-IDF Fitting:** Fits a global `TfidfVectorizer` over all cleaned dataset prompts.
4. **Query Matching:** When you type a question, your query goes through the same text preprocessing pipeline, converts into a vector, and is matched against the database using `cosine_similarity`. The highest scoring match returns its paired response.