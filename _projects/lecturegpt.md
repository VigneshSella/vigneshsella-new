---
layout: page
title: "LectureGPT: an open-source GPT-3 based AI-assistant"
description: A LLM fine-tuned on course lecture notes with retrieval augmented generation, creating a conversational AI-assistant for students to ask specific questions about their course material.
img: assets/img/publication_preview/Full_GPT_architecture.svg.png
importance: 1
category: fun
---

LectureGPT was a project I worked on to explore the NLP-world and its capabilities using standard desktop-grade hardware. By fine-tuning on lecture notes, the user can ask questions regarding course content and the LLM can respond with more specific relevant answers, ideally with notation that matches the style of the professor. The main technologies used to implement this project are:

- **Large Language Models (LLMs):** [EleutherAI/gpt-neo-125m](https://huggingface.co/EleutherAI/gpt-neo-125m) from HuggingFace Transformers library
- **Retrieval Augmented Generation (RAG):** provide course-specific information in response to user queries
- **LangChain:** to handle the pipeline of tasks required to serve user queries
- **Embeddings:** [sentence-transformers/all-MiniLM-L6-v2](https://huggingface.co/sentence-transformers/all-MiniLM-L6-v2) from HuggingFace
- **FAISS (Facebook AI Similarity Search):** efficiently [search vector database](https://huggingface.co/docs/datasets/v1.2.0/faiss_and_ea.html) (embeddings)
- **User Interface (UI):** [Gradio](https://www.gradio.app/) for a simple easy-to-set-up UI

The implementation of the project was fairly straightforward due to the well-made open-source libraries available for builders to create with. Nevertheless, I faced some challenges regarding the limits of my desktop-grade hardware. I am running LectureGPT on a Windows 10 PC with a NVIDIA GeForce RTX 4070 SUPER which has 12GB of dedicated memory. Firstly, this limited the LLM which I could fine-tune followed by the max number of tokens I could process in my input, which severely limited my documents in the RAG step. To work around these limitations, I worked with small "mini" models for the LLM and embeddings as aforementioned. Second, I broke down documents (from the course lecture notes) into much smaller segments that ideally matched with the structure of the lecture notes themselves. Lastly, I also modified the default prompt that [LangChain](https://python.langchain.com/docs/tutorials/llm_chain/) utilizes to shorten dynamically based on the size of the user-input so that at-least some output could be present. The results of the project were mildly satisfactory likely due to the underlying LLM. Future work will include deploying this to more dedicated and powerful hardware and exploring the limits of these "mini-"LLMs/embedding models.
