# TalentScout AI Hiring Assistant

Welcome to the **TalentScout AI Hiring Assistant** repository! This application is a Streamlit-based AI assistant designed to guide candidates through a series of questions to gather their information and assess their technical skills. It validates and stores the collected data in a JSON file for further review. The system also generates relevant technical questions based on the candidate's specified tech stack using a language model.

## Table of Contents
- [Overview](#overview)
- [Project Structure](#project-structure)
- [Key Components](#key-components)
- [Setup and Installation](#setup-and-installation)
- [How It Works](#how-it-works)
- [Language Model (LLM)](#language-model-llm)
- [Additional Features for Robustness](#additional-features-for-robustness)
- [License](#license)

## Overview

The **TalentScout AI Hiring Assistant** is an intelligent chatbot that helps HR teams automate candidate screening by gathering essential candidate information such as:
- Full Name
- Email Address
- Phone Number
- Years of Experience
- Desired Position(s)
- Tech Stack

The assistant then generates relevant technical questions based on the candidate's skills to evaluate their proficiency. All data is validated, stored in a JSON file, and can be reviewed for future analysis.

## Project Structure

```plaintext
hiring-assistant/
├── README.md
├── requirements.txt
├── .env
├── config.py
├── app.py
├── utils/
│   ├── __init__.py
│   ├── llm_handler.py
│   ├── conversation.py
│   ├── data_validator.py
│   └── tech_questions.py
└── templates/
    └── prompts.py
```

## Key Components
Key Components
app.py: Main Streamlit application that runs the app and manages user interactions.
conversation.py: Manages the conversation flow, handles user inputs, and transitions between different stages.
llm_handler.py: Handles interactions with the language model to generate responses.
data_validator.py: Defines the CandidateInfo model using Pydantic for data validation.
tech_questions.py: Manages the generation and retrieval of technical questions.
prompts.py: Contains predefined conversation prompts for different stages of the interaction.
Setup and Installation

1. Set Up the Environment
Clone the repository:
 ```bash
   git clone https://github.com/sasank-sasi/talent-scout-hiring-assistant.git
   cd talent-scout-hiring-assistant
```

Create a virtual environment (optional but recommended):

```bash
python -m venv venv
source venv/bin/activate 
```
    # On Windows: venv\Scripts\activate
   
Install dependencies:

```bash
pip install -r requirements.txt
```
2. Configuration
Create a .env file to store sensitive information such as API keys:
```bash
API_KEY=your_api_key_here
Update config.py to load configuration settings from the .env file.
GROQ_API_KEY=<your_api_key>
MODEL_NAME=<model_name>
you can use dotenv!
```

3. Run the Application
Start the Streamlit application:
```bash
streamlit run app.py
The app will be accessible at http://localhost:8501.
```
or you can run it live at
live: https://talentscouthire.streamlit.app

How It Works
1. Initialization
The application initializes session states, ensuring all necessary variables are set up for the conversation.
The init_session_state function ensures all session state variables are initialized.
2. User Interaction
The user starts the conversation by typing "start".
The conversation manager then guides the user through a series of questions to collect details like name, email, experience, location, position, and tech stack.
3. Technical Questions
Based on the user-provided tech stack, the assistant generates relevant technical questions to assess the candidate's expertise.
The handle_technical_questions method handles the interaction with the language model and retrieves the questions.
4. Data Validation and Storage
The data is validated using Pydantic models, ensuring all required fields are filled out correctly.
The validated data is stored in a JSON file for future review.
5. Completion
The conversation ends with a thank-you message and the collected data being stored.
Language Model (LLM)
The application uses the Groq language model to generate responses and technical questions based on the user's input.
API: Interactions with the Groq API are handled via the llm_handler.py file.
Configuration: The API key and model name are configured in the .env file and loaded into the application via config.py.
Additional Features for Robustness
1. Error Handling
Comprehensive error handling ensures that any issues are caught and users receive specific feedback. Errors are logged for debugging purposes.
2. Security
Sensitive data is secured using environment variables, and user inputs are sanitized to prevent injection attacks.
3. User Interface
The UI is enhanced with better styling and interactive elements.
Progress indicators show the user's progress through the conversation stages.
4. Data Storage
Instead of storing data in a JSON file, consider using a database (e.g., PostgreSQL, MongoDB) for better scalability and security.
5. Testing
Unit tests are written for the conversation manager and data validation logic.
End-to-end tests are used to ensure the application works as expected.
6. Extensibility
The system is designed to allow easy customization of conversation prompts and stages.
Future improvements can include support for multiple languages and a more modular design to add new features.
7. Analytics
Track user interactions and provide insights and reports on the collected data.
Implement tools to monitor user behavior and identify areas for improvement.


License
This project is licensed under the MIT License - see the LICENSE file for details.



