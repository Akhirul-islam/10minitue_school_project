# 10minitue_school_project

This project demonstrates a Bengali PDF-based Question Answering (QA) system using OCR, semantic search, and multilingual QA models.

---

## 🧰 Setup Guide
### 🔧 Install Dependencies (in Colab)
```bash
# OCR & PDF tools
!pip install pytesseract pdf2image
!apt-get install tesseract-ocr -y
!apt-get install tesseract-ocr-ben -y
!apt-get install poppler-utils -y

# NLP & RAG stack
!pip install pymupdf langchain
!pip install -U langchain langchain-community
!pip install sentence-transformers
!pip install faiss-cpu



Tools, Libraries, and Packages Used
pytesseract, pdf2image, poppler-utils – For Bengali OCR
sentence-transformers/LaBSE – Multilingual embedding
deepset/xlm-roberta-large-squad2 – Question answering model (Bangla & English)
faiss – Efficient similarity search
LangChain – Document loaders and chunking
Transformers, HuggingFacePipeline

What method or library did you use to extract the text, and why?
1st i direct upload pdf using langchain pdf upload function.but the result was noisy and it didnot extract bangla character properlt.then trying many things finally i Used pytesseract with Bengali OCR (tesseract-ocr-ben) and pdf2image. It effectively extracts Bangla text from scanned PDFs. Some formatting inconsistencies were manually resolved.

What chunking strategy did you choose and why?
in this pdf context i used differebt chunking method.but as the pdf is large and it can be chunk any where for this i Used RecursiveCharacterTextSplitter with chunk_size=1000 and overlap=200. This balances context retention with efficient retrieval. Works well for semantic matching in QA.

How are you comparing the query with your stored chunks?
Used FAISS with L2 distance over LaBSE embeddings. It's fast and effective for retrieving semantically similar chunks.

How do you ensure meaningful question-chunk comparison?
By using overlap during chunking and powerful sentence embeddings. If the query is vague or lacks context, retrieval may still surface semantically relevant chunks.

Do the results seem relevant? What might improve them?
Yes, relevant.
Improvement ideas:
Use Bangla-specific QA models (if available)
Try paragraph-based chunking for richer context
Add reranking with model confidence

I originally wanted to use an OpenAI model for the embeddings and the LLM, but I wasn’t sure how to properly use my API key in Google Colab. I tried a few different methods, but couldn’t get it to work.
To be honest, I didn’t know about Retrieval-Augmented Generation (RAG) before. I only started learning about it after receiving the project instructions via email. Since then, I’ve been doing my best to understand the concept and build the project.I’m not fully satisfied with the output yet, but this has been a great learning experience for me. I’ve learned how to build and deploy something new, and I’m proud of the effort I’ve put into it.
