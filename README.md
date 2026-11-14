# ASKWISE — buildathon prototype

ASKWISE is a browser-based prototype for the “Ask-Your-Data Analyst” brief. Open `index.html` in a modern browser, upload a CSV, TSV, or Excel workbook, then ask a question about the first sheet. The file is analyzed locally in the browser.

## What it does

- Detects text, number, and date columns.
- Handles common questions about totals, counts, averages, rankings, categories, and trends over time.
- Displays a chart, a short explanation, a result table, and the SQL-style query used for the calculation.
- Includes sample questions and supports drag and drop.
- Includes five visible question suggestions, related follow-up questions, and a persistent light/dark theme toggle.
- Supports optional voice input through the browser Speech Recognition API when available; the browser asks for microphone permission when the mic button is clicked. Speech is transcribed into the question field for review before submission.

## Prototype boundary

This MVP uses local, rule-based question parsing rather than a language model or database. Its SQL display is an equivalent, inspectable query description; the browser calculates results directly from the uploaded rows. Unrelated questions return “Question not related”; relevant questions the available data cannot answer return “Data not mentioned”. It can’t reliably interpret every phrasing or answer questions that need complex filters, joins, or causal analysis. Excel reading uses the SheetJS browser library from a CDN, so Excel uploads need an internet connection; CSV uploads do not.

For a production buildathon demo, the next step is to replace the rule-based parser with a model that maps questions to a validated query plan, execute that plan with DuckDB or another analytics engine, and keep the query/result checks visible to the user.
