# Digikala Review Analyzer

This mini-project is a Python-based tool that automatically extracts customer reviews for any product on Digikala and uses Large Language Models (LLMs) to generate a comprehensive, human-readable buyer's summary in Persian.

## Features
* **Automated Review Scraping:** Extracts the Product ID from a given Digikala URL and paginates through the Digikala API to collect all user comments.
* **Direct Persian Analysis:** Processes Farsi reviews directly without relying on translation tools.
* **Structured Data Extraction:** Uses a primary LLM prompt to extract findings into a structured JSON format, categorizing data into positive/negative aspects, quality, performance, price value, and recurring problems.
* **Smart Buyer's Summary:** Converts the extracted JSON data into a concise, actionable Persian summary for potential buyers using a secondary LLM prompt, displayed via HTML.

## Prerequisites
* Python environment (e.g., Jupyter Notebook)
* Required libraries: `requests`, `openai`, `python-dotenv`, `IPython`.
* Access to an LLM API (configured for GapGPT via `GAP_FERMIN_KEY` or a local Ollama instance).

## Usage
1. Ensure your API keys are set in the environment variables.
2. Run the notebook cells and execute the `main()` function.
3. Enter the target Digikala product URL when prompted.
4. The system will fetch the reviews, analyze them via the LLM pipeline, and output a formatted Persian review summary detailing key strengths, risks, and buyer considerations.
