# TDS Solver API

An LLM-based API that automatically solves graded assignment questions for the Tools in Data Science course at IIT Madras' Online Degree in Data Science program.

## Overview

This application provides an API endpoint that accepts questions from any of the five graded assignments in the Tools in Data Science course. It processes the questions, along with any attached files, and returns the correct answer in a JSON format that can be directly submitted to the assignment.

## Features

- Accepts questions via POST requests with multipart/form-data
- Handles file attachments (such as ZIP files containing datasets)
- Processes various question types from all five graded assignments
- Returns answers in a standardized JSON format
- Deployed on Vercel for reliable, serverless operation

## API Usage

### Endpoint

```
POST https://your-app.vercel.app/api/
```

### Request Format

The API accepts POST requests with `multipart/form-data` containing:

- `question`: The assignment question text (required)
- `file`: An optional file attachment (e.g., ZIP files, CSV files, etc.)

### Example Request

```bash
curl -X POST "https://your-app.vercel.app/api/" \
  -H "Content-Type: multipart/form-data" \
  -F "question=Download and unzip file abcd.zip which has a single extract.csv file inside. What is the value in the 'answer' column of the CSV file?" \
  -F "file=@abcd.zip"
```

### Response Format

The API returns a JSON object with a single field:

```json
{
  "answer": "1234567890"
}
```

## Local Development

### Prerequisites

- Python 3.8+
- FastAPI
- Uvicorn
- Other dependencies listed in `requirements.txt`

### Setup

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/tds-solver.git
   cd tds-solver
   ```

2. Create a virtual environment:
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

4. Set up environment variables:
   ```bash
   cp .env.example .env
   # Edit .env with your configuration
   ```

5. Run the development server:
   ```bash
   uvicorn main:app --reload
   ```

The API will be available at `http://localhost:8000/api/`.

## Deployment

This application is deployed on Vercel. To deploy your own instance:

1. Install Vercel CLI:
   ```bash
   npm i -g vercel
   ```

2. Login to Vercel:
   ```bash
   vercel login
   ```

3. Deploy the application:
   ```bash
   vercel
   ```

## Architecture

The application uses:
- FastAPI for the API framework
- LLM integration for question processing
- File handling for processing attachments
- Serverless functions for deployment

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---