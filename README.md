Brainlox Course Search API 🧠
A specialized RESTful API that performs semantic search over technical course data from Brainlox. This project uses LangChain for document orchestration, Google Generative AI for embeddings, and FAISS for efficient vector similarity search.

🚀 Overview
Traditional keyword search often fails to find relevant content if the exact words don't match. This API implements Semantic Search, allowing users to find courses based on the intent and context of their query (e.g., searching for "building apps" will find "Flutter" or "React Native" courses even if the word "app" isn't in the title).

Key Features
Automated Ingestion: Scrapes technical course data directly from Brainlox.

High-Dimensional Embeddings: Utilizes Google's text-embedding-004 model.

Vector Indexing: Uses FAISS (Facebook AI Similarity Search) for sub-millisecond retrieval.

Flask Integration: Provides a clean POST endpoint for easy integration.

🛠️ Technical Stack
Backend: Flask, Flask-RESTful

LLM Framework: LangChain

Embeddings: Google Generative AI (Gemini API)

Vector Database: FAISS (CPU)

Data Processing: NumPy, BeautifulSoup4

📥 Installation & Setup
Clone the Repository

Bash
git clone https://github.com/your-username/brainlox-search-api.git
cd brainlox-search-api
Install Dependencies

Bash
pip install flask flask-restful numpy google-generativeai langchain-community beautifulsoup4 faiss-cpu
Environment Variables (Security)
Important: Do not hardcode your API key. Create a .env file or export it in your terminal:

Bash
export GOOGLE_API_KEY="your_api_key_here"
🏃 Running the Application
Start the Server

Bash
python your_flask_file.py
Upon startup, the script will scrape the URL, chunk the text, and build the vector index in memory.

Test the Endpoint
Use curl to verify the search functionality:

Bash
curl -X POST http://127.0.0.1:5000/query \
     -H "Content-Type: application/json" \
     -d '{"query": "Mobile related development"}'
🛰️ API Reference
POST /query
Processes a natural language query and returns the top 3 most relevant document chunks.

Request Body:
| Key | Type | Description |
| :--- | :--- | :--- |
| query | string | The search term or question. |

Example Response:

JSON
[
  {
    "document": "Mastering Flutter for Cross-Platform Apps...",
    "score": 0.1245
  },
  ...
]
