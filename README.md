# VoiceX-AI-Voice-Assistant
VoiceX is an AI-powered voice assistant developed using Natural Language Processing and speech technologies. The system converts user voice commands into text, processes them, and responds using text-to-speech functionality. It supports tasks such as web searches, opening applications, and retrieving information from platforms like Google  YouTube.

#libraries 
pyttsx3
speechrecognition
pyaudio
wikipedia

main.py

from modules.speech import speak, take_command
from modules.actions import perform_action

speak("Hello, I am VoiceX. How can I help you?")

while True:
    query = take_command()
    if query == "none":
        continue

    if "exit" in query or "stop" in query:
        speak("Goodbye")
        break

    perform_action(query)

  import pyttsx3
import speech_recognition as sr

engine = pyttsx3.init()

def speak(text):
    print("VoiceX:", text)
    engine.say(text)
    engine.runAndWait()

def take_command():
    r = sr.Recognizer()
    with sr.Microphone() as source:
        print("Listening...")
        r.pause_threshold = 1
        audio = r.listen(source)

    try:
        query = r.recognize_google(audio, language="en-in")
        print("User:", query)
        return query.lower()
    except:
        print("Could not recognize")
        return "none"

    import wikipedia
import webbrowser
from modules.speech import speak

def perform_action(query):

  if "wikipedia" in query:
        speak("Searching Wikipedia")
        query = query.replace("wikipedia", "")
        try:
            result = wikipedia.summary(query, sentences=2)
            speak(result)
        except:
            speak("No results found")

  elif "open google" in query:
        speak("Opening Google")
        webbrowser.open("https://www.google.com")

  elif "open youtube" in query:
        speak("Opening YouTube")
        webbrowser.open("https://www.youtube.com")

  elif "your name" in query:
        speak("My name is VoiceX, your AI assistant")

  else:
        speak("Sorry, I did not understand the command")
        
    # VoiceX – AI Voice Assistant

VoiceX is a basic AI-powered voice assistant built using Python and NLP concepts.
It listens to voice commands, processes them, and performs actions such as web search
and Wikipedia queries.

## Features
- Voice input and speech output
- Wikipedia search
- Open Google and YouTube
- Modular and easy-to-understand code

## Technologies Used
- Python
- SpeechRecognition
- pyttsx3
- Wikipedia API

## How to Run
1. Install dependencies:
   pip install -r requirements.txt
2. Run:
   python main.py


   VoiceX: Hello, I am VoiceX AI Voice Assistant
Listening...
User: open google
VoiceX: Opening Google

Listening...
User: wikipedia artificial intelligence
VoiceX: Searching Wikipedia
VoiceX: Artificial intelligence is intelligence demonstrated by machines...

Listening...
User: stop
VoiceX: Thank you. Goodbye.
