

## Follow these steps to set up and run the project locally.


## Step 1: Create and Activate Virtual Environment

```bash
python3 -m venv .venv
source .venv/bin/activate
```

*Note: On Windows, activate the environment using:*

```bash
.venv\Scripts\activate
```

---

## Step 2: Start the Database

Make sure Docker is installed and running, then execute:

```bash
docker compose -f docker-compose.graph.db.yml up
```

This will start the database service defined in the Docker Compose file.

---

## Step 3: Install Dependencies

```bash
pip install -r requirements.txt
```

---

 # Chatbot Application with OpenAI, Memory, and Graph Database Integration

This Python script is a chatbot application that integrates with OpenAI's GPT model, a memory storage system, and a graph database. Here's a breakdown of its components and functionality:

---

## Key Components

### Imports
- **Memory**: A custom library for managing memory storage.
- **OpenAI**: A library for interacting with OpenAI's API.

### API Keys and Configuration
- `OPENAI_API_KEY`: The API key for accessing OpenAI's services.
- `QUADRANT_HOST`: Host for the vector database (Qdrant).
- `NEO4J_URL`, `NEO4J_USERNAME`, `NEO4J_PASSWORD`: Credentials for connecting to a Neo4j graph database.

### Configuration Dictionary
Defines settings for the memory client, including:
- **Embedder**: Uses OpenAI's embedding model for vector storage.
- **LLM**: Specifies the GPT model for generating responses.
- **Vector Store**: Configures Qdrant as the vector database.
- **Graph Store**: Configures Neo4j as the graph database.

### Clients
- `mem_client`: A memory client initialized with the configuration.
- `openai_client`: An OpenAI client initialized with the API key.

---

## Functionality

### `chat(message)` Function

1. **Memory Search**  
   Searches the memory database for relevant information based on the user's input (`message`).  
   Retrieves and formats the results into a string (`memories`).

2. **System Prompt**  
   Constructs a system prompt that includes the retrieved memories and defines the chatbot's behavior.

3. **OpenAI API Call**  
   Sends the system prompt and user message to OpenAI's GPT model to generate a response.

4. **Memory Update**  
   Appends the assistant's response to the conversation history and updates the memory database.

5. **Return**  
   Returns the assistant's response to the user.

### Main Loop
Continuously prompts the user for input (`message`), calls the `chat` function with the user's input, and prints the chatbot's response.

---

## Purpose

This script creates a chatbot that:

- Uses memory to provide context-aware responses.
- Stores and retrieves information from a vector database (Qdrant) and a graph database (Neo4j).
- Leverages OpenAI's GPT model for natural language understanding and response generation.

---

## Example Configuration Snippet

