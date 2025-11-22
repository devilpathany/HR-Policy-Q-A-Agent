# 🤖 HR Policy Q&A Agent

This project implements a **Retrieval-Augmented Generation (RAG) Agent** designed to answer specific employee questions by retrieving and synthesizing information from a structured HR policy document. It transforms a static PDF handbook into an interactive knowledge base, showcasing skills in modern AI and NLP.

## ✨ Core Functionality

The agent's primary function is to provide fast, accurate, and sourced answers to employee queries regarding company policies.

* **Source Document:** NovaTech Solutions Pvt. Ltd. - HR Policies & Employee Handbook.
* **Key Benefit:** Eliminates the need for employees to manually search large documents, improving HR service efficiency and compliance.

### **Policy Coverage**

The system is trained on all sections of the NovaTech HR Handbook, including:
* **Working Hours & Attendance (Section 1):** Daily schedule (9:00 AM - 5:00 PM), attendance marking procedures, and remote work limits (2 days per month).
* **Leave Policy (Section 2):** Entitlements for Annual (14 days), Sick (8 days), Casual (7 days), Maternity (12 weeks), and Paternity (7 days) leaves.
* **Employee Conduct (Section 3):** Dress code (Smart casual/Formal for clients) and the policy against unauthorized software installation.
* [cite_start]**Financial & Benefits (Section 8 & 9):** Expense limits (Meals up to $25/day) and the training sponsorship program (one course every six months)[cite: 77, 86].
* [cite_start]**Termination (Section 10):** Resignation notice period (30 days) and the timeline for receiving the experience letter (within 14 days)[cite: 89, 93].

## 💻 Technical Stack

| Component | Technology/Tool | Role in RAG Pipeline |
| :--- | :--- | :--- |
| **Data Ingestion & Processing** | Python (PyPDF, Text Splitters) | Parses the PDF and breaks text into manageable chunks. |
| **Embedding Model** | (Specify your chosen model: e.g., `HuggingFaceEmbeddings` or `OpenAIEmbeddings`) | Converts text chunks and queries into vector representations (numerical data). |
| **Vector Database** | (Specify your chosen database: e.g., `ChromaDB` or `FAISS`) | Stores the vector embeddings for fast and efficient semantic search. |
| **Orchestration** | LangChain / Custom Logic | Manages the entire RAG workflow, from query retrieval to answer synthesis. |
| **Generative Model (LLM)** | (Specify your chosen model: e.g., `GPT-3.5-Turbo`, `Gemini`) | Formulates the final, human-readable answer using the retrieved context. |

## 📐 RAG Architecture

The project utilizes a standard Retrieval-Augmented Generation pipeline. 

### **The Workflow**

1.  **Ingestion:** The HR document is parsed, chunked, and embedded. The resulting vectors are stored in the Vector Database.
2.  **Query:** The user asks a question, which is immediately embedded into a vector.
3.  **Retrieval:** The system performs a **semantic search** in the Vector Database to find the top relevant policy text chunks that are numerically closest to the query.
4.  **Generation:** The relevant chunks (Context) and the original Query are passed to the LLM. The LLM then generates an answer that is *grounded* only in the provided context, ensuring accuracy and avoiding hallucination.

## 🛠️ Getting Started

### **Prerequisites**

* Python 3.8+
* An API key for your chosen LLM (e.g., OpenAI, Cohere, etc.)

### **Installation**

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/yourusername/hr-policy-qa-agent.git](https://github.com/yourusername/hr-policy-qa-agent.git)
    cd hr-policy-qa-agent
    ```

2.  **Install dependencies:**
    ```bash
    pip install -r requirements.txt
    ```

3.  **Set Environment Variables:**
    Create a file named `.env` in the root directory and add your API key:
    ```
    # Replace with your actual key
    OPENAI_API_KEY="sk-..." 
    ```

### **Usage**

1.  **Run the Ingestion Script:** This step builds the vector database from the PDF. You only need to run this once, or whenever the source PDF is updated.
    ```bash
    python src/ingestion.py
    ```

2.  **Run the Q&A Agent:**
    ```bash
    python app.py
    ```
    The application will prompt you to enter a question.

    ***Example Interaction:***
    ```
    > Enter your question: What is the latest date I can submit my expense claims?
    > [cite_start]🤖 Agent Answer: Employees must submit all receipts and expense claims within five days of returning from the business trip. [cite: 81]
    ```

## 📂 Repository Structure
