import streamlit as st
import random

# Function to initialize or reset the game state
def reset_game():
    st.session_state.target_number = random.randint(1, 100)
    st.session_state.attempts = 0
    st.session_state.message = "Guess a number between 1 and 100!"

# Initialize session state variables
if "target_number" not in st.session_state:
    reset_game()

# App title
st.title("Number Guessing Game")

# Display message
st.write(st.session_state.message)

# Input field for the user's guess
guess = st.number_input("Enter your guess:", min_value=1, max_value=100, step=1)

# Button to submit the guess
if st.button("Submit"):
    st.session_state.attempts += 1
    if guess < st.session_state.target_number:
        st.session_state.message = "Too low! Try again."
    elif guess > st.session_state.target_number:
        st.session_state.message = "Too high! Try again."
    else:
        st.session_state.message = f"🎉 Correct! You guessed it in {st.session_state.attempts} attempts."
        if st.button("Play Again"):
            reset_game()

# Reset game button
if st.button("Reset Game"):
    reset_game()


<!---
SenthilKumaran2162006/SenthilKumaran2162006 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
