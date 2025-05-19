<div align="center">

# **Nageeb Chatbot Project**


| الرقم الأكاديمي  | الاسم                                   |
|------------------|----------------------------------------|
| 412200226      | عبدالحميد سامي رشاد عيد               |
| 412200002      | أحمد حسين على عبدالسلام                 |
| 412200261      | عمر حامد على أبوالسعود                |
| 412200005      | أحمد فوزى أمين عبدالواحد               |
| 412200025      | خلود عماد محمود غنيم                   |
| 412200013      | أنس عبدالغنى أحمد الصعيدى             |

</div>

## 💡 Project Idea & Purpose

This project scrapes structured service data from [digital.gov.eg](https://digital.gov.eg), Egypt’s official digital services platform. It collects all active e-government services, organized by category, and extracts details like service descriptions, required documents, terms, and related services, storing them in structured JSON format.

The core purpose is to power a smart chatbot that answers user queries by matching questions to the scraped data and retrieving relevant service details. This enables natural interaction with government service information without navigating the full website.

## 🎯 Project Goals

- ✅ Extract all categories and their active services.
- ✅ Scrape comprehensive service details from individual service pages.
- ✅ Handle JavaScript-rendered content for complete data extraction.
- ✅ Output clean, structured JSON files for easy querying.
- ✅ Enable question-answering via a chatbot using rule-based and TF-IDF models.

## 🧰 Libraries & Tools Used

| Tool / Library | Purpose |
| --- | --- |
| **Playwright** | Automates browser actions for JavaScript-heavy pages |
| **requests** | Handles fast HTTP requests for static HTML |
| **BeautifulSoup (bs4)** | Parses and extracts HTML content |
| **tqdm** | Displays progress bars during scraping |
| **json** | Stores data in structured JSON format |
| **collections.defaultdict** | Groups services by categories |
| **typing.TypedDict** | Defines structured output schemas |
| **re** | Cleans text using regular expressions |
| **sys** | Redirects error logs to avoid cluttering progress bars |
| **Flask** | Powers the API server for the chatbot |
| **Flask-CORS** | Enables cross-origin requests for the API |
| **scikit-learn** | Implements TF-IDF for query matching |

## 🚀 Getting Started

### Prerequisites

- Python 3.8+
- Install required dependencies:

  ```bash
  pip install -r requirements.txt
  ```

- Install Playwright browsers:

  ```bash
  playwright install
  ```

### Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/Abdo-Eid/Najeeb_chatbot.git
   cd Najeeb_chatbot
   ```

2. Install dependencies:

   ```bash
   pip install -r requirements.txt
   ```

### Usage

1. **Run the Scraper** to collect and store service data:

   ```bash
   python scraper.py
   ```

   Output JSON files are saved in the `data/` directory.

2. **Run the Flask API** for the chatbot:

   ```bash
   python app.py
   ```

   The server runs on `http://127.0.0.1:5000`.

3. **How to Run the API (Windows)**

   - 📦 **Install dependencies**  
     In the project directory, open Command Prompt or PowerShell and run:

     ```bash
     pip install -r requirements.txt
     ```

   - ▶️ **Start the Flask server**  
     Run:

     ```bash
     python app.py
     ```

     You should see:

     ```
     * Running on http://127.0.0.1:5000
     ```

## 🔗 API Endpoint

### POST `/chat`

#### Request
- **Content-Type**: `application/json`
- **Payload**:

  ```json
  {
    "message": "اهلا"
  }
  ```

#### Response
- **JSON**:

  ```json
  {
    "response": "ازيك عامل اي"
  }
  ```

## 🧪 Example Testing

### Using Python `requests`
```python
import requests

response = requests.post("http://127.0.0.1:5000/chat", json={"message": "السلام عليكم"})
print(response.json())
```

### Using `curl`
```bash
curl -X POST http://127.0.0.1:5000/chat -H "Content-Type: application/json" -d '{"message":"السلام عليكم"}'
```

### Using Postman
- **Method**: POST
- **URL**: `http://127.0.0.1:5000/chat`
- **Body** → Raw → JSON:

  ```json
  {
    "message": "باي"
  }
  ```

## 📝 Notes

- The scraper uses Playwright to handle dynamic content, ensuring all JavaScript-rendered data is captured.
- The chatbot combines rule-based responses for greetings/farewells and TF-IDF for matching real queries to services.
- If a query’s similarity score is too low, the chatbot responds with "عذراً، لم أفهم سؤالك."
- Error logs are redirected to maintain a clean progress display during scraping.
##

