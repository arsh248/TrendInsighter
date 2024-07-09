
# TrendInsighter

**TrendInsighter** is a powerful tool designed to uncover and narrate the latest trends in various industries. Using advanced AI models and customized agents, TrendInsighter provides insightful research and engaging articles on emerging topics.TrendInsighter leverages AI-driven research and writing capabilities to identify and articulate cutting-edge developments across various industries. By employing advanced agents equipped with memory and tailored AI models, it delivers comprehensive reports and engaging articles that highlight emerging technologies, market trends, and their potential impacts, fostering informed decision-making and industry insights.


## Project Overview

This project utilizes the **crewai** framework to create specialized agents for research and writing tasks. These agents are equipped with memory capabilities and a backstory to enhance their performance.

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/arsh248/TrendInsighter
   cd TrendInsighter
   ```

2. Create a virtual environment and activate it:
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows use `venv\Scripts\activate`
   ```

3. Install the required packages:
   ```bash
   pip install -r requirements.txt
   ```

4. Set up your environment variables by creating a `.env` file:
   ```dotenv
   GOOGLE_API_KEY=your_google_api_key
   SERPER_API_KEY=your_serper_api_key
   ```

## Usage

### Research Task

The research task is designed to identify groundbreaking technologies in a given topic. The `news_researcher` agent uses the `gemini-1.5-flash` model from Google Generative AI to provide comprehensive reports.

### Writing Task

The writing task is aimed at creating engaging and informative articles on the latest advancements in a given topic. The `news_writer` agent uses the same AI model to generate compelling narratives.

## Crewai Framework

**Crewai** is a versatile framework designed to simplify the creation and management of AI agents. It provides an intuitive interface for defining agents, tasks, and tools, enabling seamless integration with various AI models.

### Key Features of crewai

- **Agent Creation**: Easily define agents with specific roles, goals, backstories, and memory capabilities.
- **Task Management**: Create tasks with detailed descriptions and expected outputs, and assign them to agents.
- **Tool Integration**: Integrate custom tools to enhance the functionality of agents.
- **Flexible Execution**: Support for synchronous and asynchronous task execution.

### Example: Creating an Agent

```python
from crewai import Agent
from tools import tool
from dotenv import load_dotenv
load_dotenv()
from langchain_google_genai import ChatGoogleGenerativeAI
import os

## Call the gemini models
llm=ChatGoogleGenerativeAI(model="gemini-1.5-flash",
                           verbose=True,
                           temperature=0.5,
                           google_api_key=os.getenv("GOOGLE_API_KEY"))

# Creating a senior researcher agent with memory and verbose mode

news_researcher = Agent(
    role="Senior Researcher",
    goal='Uncover groundbreaking technologies in {topic}',
    verbose=True,
    memory=True,
    backstory=(
        "Driven by curiosity, you're at the forefront of"
        "innovation, eager to explore and share knowledge that could change"
        "the world."
    ),
    tools=[tool],
    llm=llm,
    allow_delegation=True
)

## Creating a writer agent with custom tools responsible for writing news blogs

news_writer = Agent(
  role='Writer',
  goal='Narrate compelling tech stories about {topic}',
  verbose=True,
  memory=True,
  backstory=(
    "With a flair for simplifying complex topics, you craft"
    "engaging narratives that captivate and educate, bringing new"
    "discoveries to light in an accessible manner."
  ),
  tools=[tool],
  llm=llm,
  allow_delegation=False
)
```

## File Structure

```
TrendInsighter/
├── TrendInsighter/
│   ├── __pycache__/
│   ├── venv/
│   ├── .env
│   ├── agents.py
│   ├── blog.md
│   ├── crew.py
│   ├── requirements.txt
│   ├── tasks.py
│   └── tools.py
└── README.md
```

## Contributing

We welcome contributions to TrendInsighter! Please follow these steps:

1. Fork the repository.
2. Create a new branch (`git checkout -b feature-branch`).
3. Make your changes.
4. Commit your changes (`git commit -m 'Add new feature'`).
5. Push to the branch (`git push origin feature-branch`).
6. Open a pull request.

