# LangServe Conversational ChatBot
Production-Ready Conversational Bot API using LangServe, LangSmith &amp; Pinecone VerctorDB

## Installation

## Usage

### Launching the API Swagger UI

```
http://127.0.0.1:8000/docs#/
```

### Lauching the Conversational Bot Playground

```
http://127.0.0.1:8000/rag-conversation/playground/
```

## Future Steps

- [ ] Add simple conversation memory using external Document DB (MongoDB) for multi-turn conversations.
- [ ] Add more accurately curated source documents to the ChatBot knowledge base. Then updating the VectorDB.
- [ ] Use the LangServe python  SDK to interact with the API as if it were a regular Runnable.
- [ ] Update Readme with more detailed instructions on how to use the API
- [ ] UPdate installation instructions and repo description
- [ ] Add names to the Langchain Runnable for better tracing from the LangSmith UI
- [ ] Deploy the API into AWS EC2 instance. Document the process for future reference and sharing with the community.
- [ ] Dockerize the API
- [ ] Deploy the dockerized API into AWS Lambda


