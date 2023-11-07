# LangServe Conversational ChatBot
Production-Ready Conversational Bot API using LangServe, LangSmith for pipeline and prompt monitoring &amp; Pinecone VerctorDB for knowledge base storage. This ChatBot uses the Retrieval-Augmented Generation (RAG) model for conversational retrieval, which is one of the most popular LLM use-cases. It passes both a conversation history and retrieved documents into an LLM for synthesis.

## Repository & Environment Setup

Clone the repo and install the dependencies

```bash
git clone https://github.com/MarlonCajamarca/LangServeConversationalChatBot.git
```

This project expects the following environment variables to be set in a `.env` file located at the root of the repository:

This project uses Pinecone as a vectorstore and requires that `PINECONE_API_KEY`, `PINECONE_ENVIRONMENT`, and `PINECONE_INDEX` are set.

```shell
# PINECONE VECTOR DB
PINECONE_API_KEY=YOUR_API_KEY
PINECONE_ENVIRONMENT=YOUR_ENVIRONMENT
PINECONCE_INDEX=YOUR_INDEX
```

Set the `OPENAI_API_KEY` environment variable to access the OpenAI embedding and LLM models.

```shell
# OPENAI
OPENAI_API_KEY=YOUR_API_KEY
```

(Optional) Let's now configure LangSmith. 
LangSmith will help us trace, monitor and debug LangChain applications. 
LangSmith is currently in private beta, you can sign up [here](https://smith.langchain.com/). 
If you don't have access, you can skip this section

```shell
# LANGCHAIN-LANGSMITH
LANGCHAIN_API_KEY=YOUR_API_KEY
LANGCHAIN_TRACING_V2=TRUE
LANGCHAIN_PROJECT=YOUR_PROJECT
LANGCHAIN_ENDPOINT=YOUR_ENDPOINT
```

## Usage

To use this package, you should first have the LangChain CLI installed:

```shell
pip install -U langchain-cli
```

If you are inside the app directory (`cd simetrik-knowledge-bot`), then you can spin up a LangServe instance directly by:

```shell
langchain serve
```

This will start the FastAPI app with a server is running locally at 
[http://localhost:8000](http://localhost:8000)


### Launching the API Swagger UI

We can see all endpoints at [http://127.0.0.1:8000/docs](http://127.0.0.1:8000/docs)

```bash
http://127.0.0.1:8000/docs/
```

### Lauching the Conversational Bot Playground
We can access the playground at [http://127.0.0.1:8000/rag-conversation/playground](http://127.0.0.1:8000/rag-conversation/playground)  

```bash
http://127.0.0.1:8000/rag-conversation/playground/
```

### Interact with the API as a runnable using Python SDK

Follow the Python notebook located at `simetrik-knowledge-bot/packages/rag-conversation/rag_conversation.ipynb` for an interactive example on how to interact with the API using the LangServe Python SDK.

For the sake of completeness, here is a code snippet that shows how to interact with the API using the LangServe Python SDK.

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
- [ ] Add Documentation on how to store and populate the VectorDB with the knowledge base documents. 
- [ ] Add more accurately curated source documents to the ChatBot knowledge base. Then updating the VectorDB. Checkpoint at "Alarmas.md" from the Simetrik Knowledge Bot.
- [x] Provide python notebook with LangServe python SDK usage example to interact with the API as if it were a regular Runnable.
- [x] Update Readme with more detailed instructions on how to use the API
- [x] UPdate installation instructions and repo description
- [ ] Add names to the Langchain Runnable for better tracing from the LangSmith UI
- [ ] Deploy the API into AWS EC2 instance. Document the process for future reference and sharing with the community.
- [ ] Dockerize the API
- [ ] Deploy the dockerized API into AWS Lambda


