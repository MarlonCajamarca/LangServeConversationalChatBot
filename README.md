# LangServe Conversational ChatBot
Production-Ready Conversational Bot API using LangServe, LangSmith &amp; Pinecone VerctorDB

## Installation

## Usage

### Launching the API Swagger UI

```bash
http://127.0.0.1:8000/docs/
```

### Lauching the Conversational Bot Playground

```bash
http://127.0.0.1:8000/rag-conversation/playground/
```

### Interact with the API as a runnable using Python SDK

Follow the Python notebook located at `simetrik-knowledge-bot/packages/rag-conversation/rag_conversation.ipynb` for an interactive example on how to interact with the API using the LangServe Python SDK.

For the sake of simplicity, here is a code snippet that shows how to interact with the API using the LangServe Python SDK.

```python
from langserve import RemoteRunnable

runnable = RemoteRunnable("http://localhost:8000/rag-conversation")

question = "The user question goes here"
answer = runnable.invoke(
    {
        "question": question,
        "chat_history": [],
    }
)
print(answer)
```

## Future Steps

- [ ] Add simple conversation memory using external Document DB (MongoDB) for multi-turn conversations.
- [ ] Add more accurately curated source documents to the ChatBot knowledge base. Then updating the VectorDB.
- [x] Provide python notebook with LangServe python SDK usage example to interact with the API as if it were a regular Runnable.
- [ ] Update Readme with more detailed instructions on how to use the API
- [ ] UPdate installation instructions and repo description
- [ ] Add names to the Langchain Runnable for better tracing from the LangSmith UI
- [ ] Deploy the API into AWS EC2 instance. Document the process for future reference and sharing with the community.
- [ ] Dockerize the API
- [ ] Deploy the dockerized API into AWS Lambda


