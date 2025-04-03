# My-first-assignment-project-
Streamlit project 
import streamlit as st

st.title("Hello Streamlit-er 👋")
st.markdown(
    """ 
    This is a playground for you to try Streamlit and have fun. 

    **There's :rainbow[so much] you can build!**
    
    We prepared a few examples for you to get started. Just 
    click on the buttons above and discover what you can do 
    with Streamlit. 
    """
)

if st.button("Send balloons!"):
    st.balloons()

import streamlit as st

st.badge("New")
st.badge("Success", icon=":material/check:", color="green")

st.markdown(
    ":violet-badge[:material/star: Favorite] :orange-badge[⚠️ Needs review] :gray-badge[Deprecated]"
)
import streamlit as st
import pandas as pd
import numpy as np
import streamlit as st

st.title("Streamlit Button Example")

if st.button("Click Me"):
    st.write("Button Clicked!")

import streamlit as st

# List of questions
questions = [
    "What is your favorite color?",
    "Where do you live?",
    "What is your hobby?",
    "What is your dream job?"
]

# Initialize session state for question index
if "question_index" not in st.session_state:
    st.session_state["question_index"] = 0

# Display the current question
st.write(questions[st.session_state["question_index"]])

# Button to show the next question
if st.button("Next Question"):
    st.session_state["question_index"] = (st.session_state["question_index"] + 1) % len(questions)
    st.experimental_rerun()
#streamlet
import streamlit as st
import base64

# Function to set background image
def set_bg_image(image_file):
    with open(image_file, "rb") as file:
        encoded_string = base64.b64encode(file.read()).decode()
    
    bg_image_style = f'''
    <style>
    .stApp {{
        background-image: url("data:image/png;base64,{encoded_string}");
        background-size: cover;
    }}
    </style>
    '''
    st.markdown(bg_image_style, unsafe_allow_html=True)

# Function to set background color
def set_bg_color(color):
    bg_color_style = f'''
    <style>
    .stApp {{
        background-color: {color};
    }}
    </style>
    '''
    st.markdown(bg_color_style, unsafe_allow_html=True)

# Streamlit UI
def main():
    st.title("Custom Background in Streamlit")
    
    option = st.radio("Choose Background Type:", ("Color", "Image"))
    
    if option == "Color":
        color = st.color_picker("Pick a background color", "#ffffff")
        set_bg_color(color)
    else:
        image_file = st.file_uploader("Upload Background Image", type=["png", "jpg", "jpeg"])
        if image_file:
            with open("temp_bg.png", "wb") as f:
                f.write(image_file.getbuffer())
            set_bg_image("temp_bg.png")
    
    st.write("Your background is set!")

if __name__ == "__main__":
    main()
streamlit run app.py
