#  Stephen King Books Data Extraction & Processing

A beginner-friendly Python project that demonstrates how to **fetch data from a REST API, process JSON data, convert it into a Pandas DataFrame, select required columns, and export the final data to CSV**.

The project uses the **Stephen King Books API** to collect information about Stephen King books.

---

##  Project Overview

In this project, I worked with a **REST API** to retrieve book information in **JSON format**.

The data is then:

**REST API → JSON → Pandas DataFrame → Selected Data → CSV**

---

##  Technologies Used

*  Python
*  Pandas
*  REST API
*  JSON
*  CSV

### Libraries

```python
import requests
import json
import pandas as pd
import sys
```

---

##  Project Workflow

### 1. Fetch Data from API

The `requests` library is used to send an HTTP GET request to the Stephen King Books API.

```python
url = 'https://stephen-king-api.onrender.com/api/books'

res = requests.get(url)

if res.status_code != 200:
    sys.exit('Data is not fetched successfully')

json_data = res.json()
```

### 2. Save API Data as JSON

The API response is saved locally as `book_data.json`.

```python
with open('book_data.json', 'w+', encoding='utf-8') as f:
    json.dump(res.json(), f, indent=4)
```

### 3. Convert JSON into DataFrame

The book records are converted into a Pandas DataFrame using `json_normalize()`.

```python
df = pd.json_normalize(json_data['data'])
```

### 4. Select Required Columns

Only the required columns are selected for the final dataset.

```python
selected_df = df[['id', 'Year', 'Title', 'Publisher']]
```

### 5. Export Data to CSV

The processed data is exported to a CSV file.

```python
selected_df.to_csv('book_data.csv', index=False)
```

---

## Project Structure

```text
stephen-king-books-api/
│
├── README.md
├── project_level_1.ipynb
├── book_data.json
└── book_data.csv
```

---

##  Output

The final dataset contains the following columns:

* `id`
* `Year`
* `Title`
* `Publisher`

Example:

| id | Year | Title       | Publisher |
| -: | ---: | ----------- | --------- |
|  1 | 1974 | Carrie      | Doubleday |
|  2 | 1975 | Salem's Lot | Doubleday |
|  3 | 1977 | The Shining | Doubleday |

---

##  Key Concepts Learned

* Working with REST APIs
* Sending HTTP GET requests
* Handling JSON responses
* Saving JSON data to a file
* Reading JSON data
* Converting JSON data into a Pandas DataFrame
* Selecting DataFrame columns
* Exporting data to CSV
* Basic data extraction and processing

---

##  Future Improvements

* Add more data analysis and visualizations
* Handle API errors more extensively
* Add automated data updates
* Perform exploratory data analysis (EDA)
* Build a simple dashboard using the extracted data

---

##  Author

**Lokesh Kumar Swami **

This project was created as a learning project to practice **Python, APIs, JSON, and Pandas**.
