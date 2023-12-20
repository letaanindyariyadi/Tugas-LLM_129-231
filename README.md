# TEXT SUMMARIZATION_129&231
<!-- PROJECT LOGO -->
<br />
<div align="center">
    <img src="logo leta.png" alt="Logo" width="360" height="180">

<h1 align="center">TEXT SUMMARIZATION</h1>
  <p align="center">
    This project focuses on summarizing text .
  </p>
</div>

Welcome to the Text Summarixation! This Streamlit application integrates with Google's Generative AI to 

## Features
Multiple Programming Languages: Choose from Python, Go, JavaScript, or TypeScript.
User-Friendly Interface: A simple and intuitive Streamlit sidebar for input.
Customizable Prompts: Specify what you want to code, and Code Writer will generate the corresponding script.
Advanced AI Integration: Utilizes Google's Generative AI to ensure high-quality code generation.
## How to Use
Select a Programming Language: Use the dropdown in the sidebar to choose your preferred language.
Enter Your Prompt: In the text input field, describe what you want to code.
Generate Code: Click the 'Generate' button to produce the code based on your prompt.
View the Result: The generated code will be displayed on the main screen.
## Installation
To run Text Summarization, you need to install Streamlit and set up the Google Generative AI API:

    pip install streamlit

    pip install google.generativeai

Set up your API key as per Google's Generative AI documentation and include it in the application (api.py file).

## Usage Example
   import streamlit as st
import google.generativeai as genai
from api import api

# Configure the API key
genai.configure(api_key=api)

# Set default parameters for text summarization
defaults = {
    'model': 'models/text-bison-001',  # Replace with a supported text summarizer model
    'temperature': 0.25,
    'candidate_count': 1,
    'top_k': 40,
    'top_p': 0.95,
}

st.title('Text Summarizer')
st.write('You can ask me to summarize any text')
final_response = None

# Creating a side panel for inputs
with st.sidebar:
    st.write("## Text Summarizer Settings")
    # Create a text input for the text to be summarized
    text_to_summarize = st.text_area("Enter the text to be summarized:")
    # When the 'Summarize' button is pressed, generate the summary
    if st.button('Summarize'):
        # Include the language in the prompt
        formatted_prompt = f"Write a code summary in English: {text_to_summarize}"
        response = genai.generate_text(
            **defaults,
            prompt=formatted_prompt
        )
        final_response = response

if final_response is not None:
    st.write(final_response.result)
## Support
For any queries or support, please open an issue on the project's GitHub repository.

## License
This project is licensed under the MIT License - see the LICENSE file for details.

# Enjoy coding with Code Writer! 🚀





