import nltk
from nltk.chat.util import Chat, reflections
import time
import random

jokes_responses = {
    "I told a chemistry joke once.": "I didn't get much of a reaction.",
    "Why don't scientists trust atoms? ": "Because they make up everything!",
    "How does a penguin build its house? ":  "Igloos it together!",
    "Parallel lines have so much in common. ":  "It’s a shame they’ll never meet.",
    "Why did the scarecrow win an award? ": "Because he was outstanding in his field!!",
    "I told my wife she should embrace her mistakes.":  " She gave me a hug.",
    "What do you call fake spaghetti? ": "An impasta!",
}

last_joke_told = None

pairs = [
    [
        r"my name is (.*) and you ?",
        ["chatbot: Hello %1,I am a bot created by yasmin. You can call me Chatbot. How are you today?",]
    ],
    [
        r"hi|hey|hello",
        ["chatbot: Hello, what is your name?", "Hey there,what is your name?",]
    ],
    [
        r"how are you?",
        ["chatbot: I'm doing well, thank you. How can I help you?",]
    ],
    [
        r"sorry (.*)",
        ["It's alright", "No problem",]
    ],
    [
        r"I am fine|fine",
        ["chatbot: Great to hear that. How can I assist you today?",]
    ],
    [
        r"what can you do|what do you do?",
        ["chatbot: I can provide information, tell jokes, or even check the weather for you.",]
    ],
    [
        r"tell me a joke",
        list(jokes_responses.keys())
    ],
    [
        r"another joke|new joke",
        list(jokes_responses.keys())
    ],
    [
        r"weather|weather like",
        ["chatbot: Sure, which city's weather would you like to know about?",]
    ],
    [
        r"Tunisia",
        ["chatbot: Clear weather with some clouds.",]
    ],
    [
        r"bye|goodbye",
        ["chatbot: Bye! Take care.",]
    ], 
    [
        r"quit",
        ["chatbot: Bye! Take care.",]
    ],
    [
        r".*",
        ["chatbot: I'm sorry, I don't understand that. Could you please ask something else?",]
    ],

]



def chatbot_response(user_input):
    global last_joke_told
    
    chat = Chat(pairs, reflections)
    response = chat.respond(user_input)
    
    if user_input.lower() in ["tell me a joke", "another joke", "new joke"]:
        jokes = list(jokes_responses.keys())
        if user_input.lower() in ["tell me a joke", "new joke"] or not last_joke_told:
            joke = random.choice(jokes)
            last_joke_told = joke
        else:
            jokes.remove(last_joke_told)
            joke = random.choice(jokes)
            last_joke_told = joke
            
        print("chatbot: Let me think of a good one...")
        time.sleep(2)
        print(joke)
        time.sleep(2) 
        print(jokes_responses[joke])
        response = None

    return response

def chatbot():
    print("chatbot: Hi! I am a simple chatbot. Type 'quit' to exit.")
    
    while True:
        user_input = input("You : ")
        
        if user_input.lower() in ["bye", "goodbye", "exit", "quit"]:
            print("chatbot: Bye! Take care.")
            break
        else:
            response = chatbot_response(user_input)
            if response:
                print(response)

if __name__ == "__main__":
    chatbot()
