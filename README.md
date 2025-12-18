AI Trip Planner

AI Trip Planner is an agent based travel planning application that generates structured, day wise itineraries for any destination using real time signals and tool assisted reasoning. It combines an interactive UI with an API layer and a LangGraph powered agent workflow to orchestrate planning steps such as weather checks, attraction discovery, currency conversion, and budget estimation.

What it does

Generates a day wise itinerary for a selected city and trip duration

Pulls real time weather to inform planning decisions

Discovers attractions and activities based on location context

Converts currency to the user’s preferred denomination

Estimates costs and produces a consolidated trip summary

System design

The application is implemented as a modular agent workflow.

LangGraph models the workflow as a graph of nodes and edges

Nodes encapsulate planning steps such as weather lookup, place search, and cost calculation

Edges define execution order and routing

A shared state object flows through the graph so each step can read and enrich the plan

This structure keeps the system extensible. New tools can be added without rewriting the full workflow.

Tech stack

Python 3.10+

LangGraph for agent workflow orchestration

FastAPI and Uvicorn for backend APIs

Streamlit for the interactive UI

Pandas for data handling

uv for fast environment and dependency management

Repository structure
AI-Trip-Planner/
├── streamlit_app.py
├── main.py
├── agent/
│   └── agentic_workflow.py
├── tools/
│   ├── weather_info_tool.py
│   ├── place_search_tool.py
│   ├── currency_conversion_tool.py
│   └── calculator_tool.py
├── prompt_library/
│   └── prompt.py
├── config/
│   └── config.yaml
├── utils/
│   ├── model_loader.py
│   ├── config_loader.py
│   └── save_to_document.py
└── README.md


Setup
Prerequisites

Python 3.10+

Git

If you use conda, deactivate it before continuing:

conda deactivate

Create and activate a virtual environment (uv)

Install uv:

pip install uv


Create a virtual environment:

uv venv env


Activate:

Windows

env\Scripts\activate


macOS or Linux

source env/bin/activate

Install dependencies

If you maintain a requirements file:

uv pip install -r requirements.txt


Or install core packages directly:

uv pip install langgraph langchain fastapi uvicorn streamlit pandas pyyaml python-dotenv

Run locally

Streamlit UI:

streamlit run streamlit_app.py


FastAPI backend:

uvicorn main:app --reload --port 8000

Configuration and secrets

Create a .env file locally and keep it out of version control. Depending on which tools you enable, you may need:

OPENAI_API_KEY or GROQ_API_KEY

TAVILY_API_KEY

OPENWEATHER_API_KEY

EXCHANGE_RATE_API_KEY

GOOGLE_PLACES_API_KEY or FOURSQUARE_API_KEY

LANGCHAIN_API_KEY (optional, for tracing)
