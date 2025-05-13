# Chat with MySQL/CSV/MongoDB/PostgreSQL - Pulzion-2024 Web N App

### Overview

This project presents a dynamic, data-driven chat interface built using Streamlit, designed to enable users to interact with multiple data sources using natural language inputs. The system supports querying MySQL databases, PostgreSQL databases, CSV files, and MongoDB collections, offering a seamless user experience through both text and voice inputs. The application is structured to switch between these data sources in real time, ensuring that users can analyze data from diverse origins without navigating complex database tools or query languages.

### MySQL and PostgreSQL Querying

The platform allows users to connect directly to either a MySQL or PostgreSQL database by entering valid credentials. Once connected, users can enter questions in plain English, which the system intelligently converts into executable SQL statements using large language models. This approach simplifies data retrieval by allowing users without SQL knowledge to interact with structured databases.

### CSV File Upload and Querying

Users can upload CSV files to the application and query them using natural language. The system reads the uploaded files, displays their schema, and enables dynamic querying using simple questions. Internally, the platform uses Pandas to handle and process data accurately based on user queries.

### MongoDB Integration

The system also connects to MongoDB, enabling users to access and query NoSQL datasets. Users can specify connection parameters and select a collection. Natural language queries are translated into appropriate MongoDB queries, allowing document-level filtering and retrieval based on flexible user prompts.

### Voice Input Support

Voice input enhances accessibility and usability by letting users speak their queries. The app captures audio using the SoundDevice library and converts it into text using speech recognition. The transcribed query is then processed as if typed, allowing for hands-free interaction with databases.

### Data Source Switching

The application is capable of dynamic data source switching. Users can seamlessly transition between MySQL, PostgreSQL, CSV, and MongoDB. Each switch clears previous context and history, ensuring the chat logic and data access are always aligned with the active data source.

### Natural Language Processing

The NLP pipeline is powered by Langchain and ChatGroq. These tools understand the schema of connected databases and generate valid SQL or MongoDB queries from user prompts. The models ensure contextual understanding and query correctness. Additionally, error handling mechanisms alert users to invalid configurations or failed queries.

### Technology Stack

| **Component**       | **Technology**       | **Description**                                                 |
| ------------------- | -------------------- | --------------------------------------------------------------- |
| **Frontend**        | Streamlit            | Web interface for user interactions and real-time data querying |
| **NLP Framework**   | Langchain + ChatGroq | Converts natural language inputs into database-specific queries |
| **Relational DBs**  | MySQL, PostgreSQL    | Handle structured data using SQL-based query execution          |
| **NoSQL DB**        | MongoDB              | Supports querying semi-structured document data                 |
| **File Handling**   | Pandas               | Reads and processes CSV files, supports schema introspection    |
| **Audio Capture**   | SoundDevice          | Captures voice input from the user                              |
| **Speech to Text**  | SpeechRecognition    | Transcribes audio to text for NLP processing                    |
| **SQL Connectors**  | PyMySQL, Psycopg2    | Executes queries on MySQL and PostgreSQL databases              |
| **Mongo Connector** | PyMongo              | Communicates with MongoDB for document-level data access        |
| **Config Handling** | dotenv               | Loads environment variables for credentials and configuration   |

### Setup and Running Instructions

To run this project locally, follow these steps:

1. **Clone the repository**

   ```bash
   git clone https://github.com/your-username/chat-with-mysql-csv-mongodb.git
   cd chat-with-mysql-csv-mongodb
   ```

2. **Create and activate a virtual environment**

   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows, use venv\Scripts\activate
   ```

3. **Install project dependencies**

   ```bash
   pip install -r requirements.txt
   ```

4. **Create a `.env` file and configure your environment variables**

   Example configuration:

   ```env
   GROQ_API_KEY=<Your ChatGroq API Key>
   DB_HOST=<MySQL/PostgreSQL Host>
   DB_PORT=<MySQL/PostgreSQL Port>
   DB_USER=<MySQL/PostgreSQL Username>
   DB_PASSWORD=<MySQL/PostgreSQL Password>
   DB_NAME=<MySQL/PostgreSQL Database Name>
   MONGO_DB_URI=<Your MongoDB Connection URI>
   MONGO_DB_NAME=<Your MongoDB Database Name>
   ```

5. **Run the Streamlit application**

   ```bash
   streamlit run app.py
   ```

6. **Open the application in your browser**
   Visit: [http://localhost:8501](http://localhost:8501)

### Future Enhancements

To further improve the system’s performance and scalability, future versions of this application can adopt the MCP (Model-Context-Prompt) framework. This approach separates the core components of the language model interaction: the model (e.g., ChatGroq), the context (database schema and configuration), and the prompt (user input). By decoupling these elements, the system becomes more modular, adaptable, and efficient. It also allows for richer schema understanding, context persistence, and better multi-database orchestration.

