### An LLM-powered application which takes user queries related to company performance metrics and converts them into a structured JSON format ✨

### Features: 🪄
1. Uses Google Gemini API to process user queries.
2. The application is able to extract the following information from user queries:
- Entity: The company name mentioned in the query (e.g., Flipkart, Amazon).
- Parameter: The performance metric mentioned in the query (e.g., GMV, revenue, profit).
- Start Date: The start date of the time period for which the metric is requested.
- End Date: The end date of the time period for which the metric is requested.
3. If the user query does not explicitly mention the start date and/or end date, it assumes the following defaults:
- Start Date: Today's date minus one year.
- End Date: Today's date.
4. The extracted information is converted into a JSON format with the following structure:
```
[
{
    "entity": "<company_name>",
    "parameter": "<metric_name>",
    "startDate": "<start_date_iso>",
    "endDate": "<end_date_iso>"
}
]
```

5. If the user query mentions multiple companies or requests a comparison, the JSON output will include multiple objects, one for each company mentioned.
6. The start date and end date are converted to the ISO 8601 format (YYYY-MM-DD).
7. The LLM understands the user query and extract relevant information, while Python is used for data manipulation and JSON conversion.

### Example Usage: 🤸‍♂️

```
User: Get me Flipkart’s GMV for the last one year
Output:
[
{
    "entity": "Flipkart",
    "parameter": "GMV",
    "startDate": "2023-05-02",
    "endDate": "2024-05-02"
}
]

User: compare this with amazon
Output:
[
{
    "entity": "Flipkart",
    "parameter": "GMV",
    "startDate": "2023-05-02",
    "endDate": "2024-05-02"
},
{
    "entity": "Amazon",
    "parameter": "GMV",
    "startDate": "2023-05-02",
    "endDate": "2024-05-02"
}
]
```

### Additional Features: 🚀

- Handles variations in user queries, such as different spellings or abbreviations of company names and metric parameters.
- Implements error handling for cases where the LLM fails to extract the necessary information from the user query.
- Considered a history length of 4 messages while processing the given query.
- Considered adding support for additional date formats or relative date ranges (e.g., "last quarter", "previous month").
