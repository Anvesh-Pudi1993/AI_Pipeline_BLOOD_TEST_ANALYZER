#  AI_Pipeline Based Blood Report Analysis User Guide 

## Overview

The Medical Report Analysis app is a comprehensive tool designed to analyze blood test reports from PDF files. Built using the Streamlit framework, this application processes the data extracted from the PDF and delivers a detailed analysis, which includes key medical findings, potential health concerns, recommended follow-up tests, actionable lifestyle advice, and references to trusted medical resources. The goal of this application is to provide users with insights into their health based on their blood test reports and to offer guidance on necessary steps for improving or maintaining their health.

## Features

- **PDF Upload:** Users can upload their blood test reports in PDF format, which the app will analyze.
- **Detailed Analysis:** The app leverages the CrewAI framework, involving specialized agents, to parse and analyze the report data, providing a comprehensive summary of the results.
- **Health Recommendations:** Based on the analysis, the app generates personalized health advice, including lifestyle modifications and suggested medical follow-ups.
- **Trusted Resources:** The app includes references to high-quality medical articles and resources, allowing users to further understand their health conditions.

## Application Workflow

1. **Data Extraction:** The app uses PyPDF2 to extract text data from the uploaded PDF files.
2. **Analysis:** Leveraging CrewAI, the app processes the data through various agents, each responsible for specific tasks such as summarizing key findings, identifying health concerns, and providing recommendations.
3. **Output:** The processed data is then displayed on the Streamlit interface, categorized into key findings, main health concerns, additional tests or follow-ups, lifestyle advice, and trusted medical resources.
## Model used 
Gemini 1.5 Flash (which can handle larger inputs)

Gemini 1.5 Flash is used in this project mainly because:

Larger Input Handling: Gemini 1.5 Flash can process much longer documents (like full blood test reports) in a single request, which is important for medical PDFs.
Speed: It is optimized for fast responses, which improves user experience in interactive apps like Streamlit.
Cost Efficiency: Gemini 1.5 Flash is designed to be more cost-effective for high-volume or large-context applications.

Why not GPT-4.0?

Context Limit: GPT-4.0 (especially the public OpenAI API) has a smaller context window, so it may not handle large medical reports as effectively.
Integration: This project is set up for Google’s Gemini API, not OpenAI’s GPT-4.0, so switching would require code and API changes.
Performance: For document analysis tasks, Gemini 1.5 Flash may provide better performance and scalability.
## Installation

### Prerequisites

Ensure that you have Python 3.8 or above installed on your machine.

### Step-by-Step Guide

   
1. **Install Dependencies:**
   Use the following command to install the required Python packages:
   ```bash
   pip install -r requirements.txt
   ```

2. **Environment Variables:**
   Create separate virtual environment for installing dependencies
   Create a `.env` file in the root directory of the project and add your environment variables:
   ```plaintext
   GEMINI_API_KEY='your_gemini_api_key' 
   This key can be used for testing purpose GEMINI_API_KEY='AIzaSyCdV6LYrVSCXnfx7iNTcQKHL6bWBmk-EB8'
   ```

3. **Run the Application:**
   Launch the Streamlit application by running the following command:
   ```bash
   streamlit run main.py
   ```

4. **Access the App:**
   Once the app is running, open the provided URL in your web browser to access the application.

## Usage

1. **Uploading a PDF Report:**
   - Navigate to the app in your web browser.
   - Upload your blood test report using the provided file uploader.
   
2. **Analyzing the Report:**
   - Click the "Analyze Report" button to start the analysis.
   - The app will process the report and provide detailed insights, including:
     - **Summary of Key Findings:** Highlighting the essential observations from the blood test.
     - **Main Health Concerns:** Listing potential health issues based on the test results.
     - **Recommended Additional Tests or Follow-Ups:** Suggesting further medical tests or follow-ups if needed.
     - **Actionable Lifestyle Advice:** Offering advice on lifestyle changes that could improve or maintain your health.
     - **References to Medical Resources:** Providing links to trusted medical articles for further reading.

## Project Structure

```
AI_Pipeline_BLOOD_TEST_ANALYZER/
│
├── app.py               # Main application script
├── agents.py            # Definitions of CrewAI agents
├── tasks.py             # Task definitions for CrewAI
├── requirements.txt     # List of Python dependencies
├── .env                 # Environment variables
├── README.md            # Project documentation
|── CBC-sample-report.pdf # sample blood test report for analyzing 
└── Streamlit_Bloodreport_Analyzer_AI_Pipeline.png      # Streamlit app interface for blood test report analysis and recommendations
```

## Key Challenges

Data Privacy: Handling sensitive medical data requires strict privacy and security measures.
Input Quality: Uploaded images or PDFs may be low quality, affecting extraction and analysis accuracy.
Error Handling: Current fallback analysis is basic and may not meet user needs in case of repeated API failures.
Model Limitations: The generative model may not always provide clinically accurate or actionable recommendations.

## Assumptions
Users have a valid Gemini API key set in their environment.
Uploaded files are genuine medical reports (images or PDFs).
The model can interpret both text and image inputs effectively.
Users understand that the analysis is for informational purposes, not a substitute for professional medical advice.

## Improvement ideas

Input Validation: Add checks for file size, format, and image clarity before processing.
Security Enhancements: Ensure temporary files are securely deleted and consider encrypting sensitive data.

User Guidance: Offer tooltips or examples to help users upload optimal files.
Explainability: Integrate model explanation tools (e.g., highlight key findings in the report).
Batch Processing: Allow multiple files to be analyzed in one session.

Logging & Monitoring: Track usage and errors for maintenance and improvement.

Model Updates: Periodically update or fine-tune the model for improved medical accuracy.


