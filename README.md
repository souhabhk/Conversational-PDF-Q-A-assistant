# Conversational-PDF-Q-A-assistant
Ever wished you could just TALK to a PDF? I did, so I built it. 



I just shipped a conversational PDF Q&A assistant powered by RAG and a multi-tool AI agent. You load any document, and the system intelligently routes your query to the right tool: answering questions, summarizing content, searching by keyword, or mapping out main topics Automatically.



What made this genuinely intresting to build:



- Stacking a ConversationalRetrievalChain inside a tool-calling agent isn't standard. The tricky part? Two memory layers running in parallel, the agent's chat history and the chain's ConversationBufferMemory. Getting them to stay in sync across conversations took real architectural thinking.



- MMR (Maximal Marginal Relevance) retrieval instead of naive top-k. The difference matters: without it, you hand the LLM 5 near-identical chunks and wonder why the answers feel shallow.



- Pinning httpx==0.27.2 to fix a silent OpenAI SDK crash (unexpected keyword argument 'proxies', openai 1.54.x breaks on httpx ≥ 0.28). That one cost me an hour. Documenting it so it doesn't cost you one.



The full pipeline:

PDF → PyPDFLoader → RecursiveCharacterTextSplitter ( chunks / overlap) → text-embedding-3-small → Chroma → ConversationalRetrievalChain + MMR → OpenAI Tools Agent → Chat UI



This is the kind of project that teaches you more about LLM systems than a tutorial.

🔗 Full code on GitHub: [your link here]



Stack: Python · LangChain · OpenAI GPT-4 · ChromaDB 



#LangChain #RAG #LLMEngineering #AI #OpenAI #VectorSearch #NLP #Python #ChromaDB 
