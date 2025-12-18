Perfect. Below is a **fully structured, visually clean, copy-paste ready README** with **clear section dividers**, consistent headings, and a professional open-source look.
AI Trip Planner
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Overview
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

AI Trip Planner is an agent-based travel planning application that generates structured, day-wise itineraries for any destination using real-time data and tool-assisted reasoning.

The project demonstrates how to design and build a modular, end-to-end **agentic AI system** using a graph-based workflow, modern LLM tooling, and clean software architecture principles.


Key Features
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

* Day-wise itinerary generation for any city
* Real-time weather lookup
* Attraction and activity discovery
* Currency conversion and budget estimation
* Modular, graph-based agent workflow
* Interactive Streamlit user interface
* API-first backend design

How the System Works
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
The core logic is implemented as an **agent workflow modeled as a directed graph**.

* **Nodes** represent individual planning steps such as weather lookup, place discovery, or cost calculation
* **Edges** define execution order and dependencies between steps
* A shared **state object** flows through the graph and is incrementally enriched
* Each node can invoke tools or external APIs independently

This design allows multiple specialized agents to collaborate toward a single goal while remaining loosely coupled and easy to extend.

Technology Stack
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Core
-----
* Python 3.10+
* LangGraph for agent orchestration
* LangChain for LLM integration

Backend
--------
* FastAPI
* Uvicorn (ASGI server)

Frontend
---------
Streamlit

Utilities
----------
* Pandas for data processing
* uv for fast environment and dependency management


Repository Structure
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

AI-Trip-Planner/
│
├── streamlit_app.py               # Streamlit UI
├── main.py                        # FastAPI backend entry point
├── requirements.txt
├── setup.py
│
├── agent/
│   └── agentic_workflow.py        # LangGraph workflow
│
├── tools/
│   ├── weather_info_tool.py
│   ├── place_search_tool.py
│   ├── currency_conversion_tool.py
│   ├── arithmetic_operation_tool.py
│   └── calculator_tool.py
│
├── prompt_library/
│   └── prompt.py                  # Prompt templates
│
├── config/
│   └── config.yaml                # Configuration values
│
├── utils/
│   ├── model_loader.py
│   ├── config_loader.py
│   ├── currency_converter.py
│   ├── place_info_search.py
│   └── save_to_document.py
│
├── logger/
│   └── logger.py                  # Custom logging
│
├── exception/
│   └── exception_handling.py      # Custom exception handling
│
└── README.md

Prerequisites
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

* Python 3.10 or higher
* Git

Environment Setup
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Install uv

```bash
pip install uv
```
Create a Virtual Environment

```bash
uv venv env
```

Activate the environment:

Windows

```bash
env\Scripts\activate
```

macOS / Linux**

```bash
source env/bin/activate
```

Install Dependencies
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Using a requirements file:

```bash
uv pip install -r requirements.txt
```

Or install core dependencies directly:

```bash
uv pip install langgraph langchain fastapi uvicorn streamlit pandas pyyaml python-dotenv
```

Running the Application
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Run the Streamlit UI
--------------------
```bash
streamlit run streamlit_app.py
```

Run the FastAPI Backend
-----------------------
```bash
uvicorn main:app --reload --port 8000
```

Environment Variables
---------------------
Create a `.env` file locally. Do **not** commit it to version control.

Depending on enabled features, you may need:

```
OPENAI_API_KEY or GROQ_API_KEY
TAVILY_API_KEY
OPENWEATHER_API_KEY
EXCHANGE_RATE_API_KEY
GOOGLE_PLACES_API_KEY or FOURSQUARE_API_KEY
LANGCHAIN_API_KEY   # Optional (for tracing and observability)
```

Extensibility and Customization
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

This project is intentionally modular and can be extended by:

* Adding new tools as graph nodes
* Swapping LLM providers without changing workflow logic
* Introducing caching or persistence layers
* Adding observability and tracing
* Deploying to cloud platforms with CI/CD pipelines

