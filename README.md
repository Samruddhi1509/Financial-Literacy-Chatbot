# Financial Literacy Chatbot - Money Mentor

Money Mentor is an AI-powered financial education companion built with Streamlit. It uses natural language processing and real-time market data to provide users with financial definitions, investment comparisons, stock market data, and financial text summarization.

## Features

- **Concept Explanation:** Explains financial terms in a concise, simple manner, using analogies where possible. Provides source recommendations and follow-up questions.
- **Market Data:** Fetches real-time stock prices, volume, and 7-day historical performance using Yahoo Finance.
- **Investment Comparison:** Compares two or more financial entities (e.g., Apple vs. Tesla) by presenting their market data and generating an expert GPT-4 analysis on risk, returns, fees, and target investors.
- **Article Summarization:** Summarizes long financial articles or text to make them understandable for beginner investors.
- **Entity Recognition:** Leverages spaCy to extract relevant organizations and financial entities from user queries.
- **Semantic Search:** Uses FAISS and OpenAI embeddings to retrieve accurate definitions from a custom financial glossary.

## Technologies Used

- **Frontend:** Streamlit
- **AI/NLP:** OpenAI API (GPT-4-Turbo, Text-Embedding-Ada-002), spaCy (`en_core_web_sm`)
- **Vector Database:** FAISS (Facebook AI Similarity Search)
- **Market Data:** yfinance
- **Data Processing:** Pandas, NumPy

## Prerequisites

- Python 3.8+
- An OpenAI API Key

## Setup Instructions

1. **Clone the repository:**
   ```bash
   git clone <repository-url>
   cd <repository-directory>
   ```

2. **Install dependencies:**
   It is recommended to use a virtual environment.
   ```bash
   pip install streamlit faiss-cpu openai numpy pandas spacy python-dotenv yfinance
   python -m spacy download en_core_web_sm
   ```

3. **Configure Environment Variables:**
   Create a `.env` file in the root directory and add your OpenAI API key:
   ```env
   OPENAI_API_KEY=your_openai_api_key_here
   ```

4. **Prepare the Data:**
   The application requires a FAISS index (`faiss_index.idx`) and its metadata (`faiss_metadata.pkl`). Ensure these files are present in the root directory alongside `app(updated).py`. 

5. **Run the Application:**
   Start the Streamlit server:
   ```bash
   streamlit run "app(updated).py"
   ```

## Usage Examples

Once the application is running, you can type queries like:

- *"What is a Roth IRA?"*
- *"Compare Apple and Tesla stock."*
- *"Give me the market data for Google."*
- Paste a long financial news article and ask it to summarize.

## Project Structure

- `app(updated).py`: Main Streamlit application file.
- `embeddings.py`: Script to generate OpenAI embeddings for the financial glossary.
- `financial_glossary.csv`: The base dataset containing financial terms and their definitions.
- `faiss_index.idx`: The pre-computed FAISS vector index (required).
- `faiss_metadata.pkl`: The pickled metadata for the FAISS index (required).
