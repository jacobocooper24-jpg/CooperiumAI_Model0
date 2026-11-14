CooperiumAI Research Assistant

A command-line AI research agent built with Python, LangChain and Claude. Give it a topic and it searches the web and Wikipedia, then returns a structured research summary with sources, and can save the results to a text file.

Features
Claude-powered agent using ChatAnthropic and a tool-calling agent
Web search via DuckDuckGo, with automatic retries so a flaky search backend doesn't crash the run
Wikipedia lookup for quick background information
Save to file tool that appends timestamped research output to research_output.txt
Structured output parsed into a Pydantic model with four fields: topic, summary, sources and tools_used
Example output
topic='Hammerhead sharks'
summary='...'
sources=['...', '...']
tools_used=['search_tool']
Getting started
Prerequisites
Python 3.10 or newer
An Anthropic API key with some credit on it (create one at console.anthropic.com)
Installation
bash
git clone https://github.com/jacobocooper24-jpg/CooperiumAI_Model0.git
cd CooperiumAI_Model0

python -m venv venv

# Windows (PowerShell)
.\venv\Scripts\Activate.ps1
# macOS / Linux
source venv/bin/activate

pip install -r requirements.txt
Configuration

Copy .env.example to .env and add your own key:

ANTHROPIC_API_KEY=your-key-here

The .env file is listed in .gitignore, so your key is never committed. Never share it or post screenshots that show it.

Run it
bash
python main.py

When prompted, type the topic you want to research.

Project structure
File	Purpose
main.py	Builds the prompt, agent and executor, then parses the response into a structured result
tools.py	Defines the search, Wikipedia and save-to-file tools
requirements.txt	Python dependencies
.env.example	Template for the environment variables you need
Changes from the original tutorial

This project is based on Tech With Tim's tutorial, but the original code no longer runs against current library versions, so it has been updated for 2026:

Updated the Claude model name, since the one in the tutorial has been retired
Moved AgentExecutor, create_tool_calling_agent and Tool to the langchain-classic package, as they were removed from langchain 1.x
Switched search to the ddgs package and wrapped it in a retry loop that fails gracefully
Fixed response parsing for the current message format
Raised the Wikipedia result length limit so answers aren't cut short
Added .gitignore and .env.example so API keys stay out of version control
Credits

Inspired by Tech With Tim's "Python AI Agent From Scratch" tutorial and his original repository. Thanks to Tim for the excellent walkthrough.

Licence

This project is licensed under the MIT License. See the LICENSE file for details.

Copyright (c) 2026 Jacob Cooper
