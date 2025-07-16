# chatbot
def chatbot():
    print("Chatbot: Hello! I am a simple chatbot. Type 'bye' to exit.")

    while True:
        user_input = input("You: ").lower()

        # Exit condition
        if user_input in ["bye", "exit", "quit"]:
            print("Chatbot: Goodbye! Have a great day.")
            break

        # Predefined rules
        elif "hello" in user_input or "hi" in user_input:
            print("Chatbot: Hello there! How can I help you?")
        elif "how are you" in user_input:
            print("Chatbot: I'm just a bot, but I'm doing fine! Thanks for asking.")
        elif "your name" in user_input:
            print("Chatbot: I'm ChatBot, your virtual assistant.")
        elif "help" in user_input:
            print("Chatbot: I can respond to greetings and simple questions like 'how are you' or 'what's your name'.")
        elif "time" in user_input:
            from datetime import datetime
            print("Chatbot: The current time is", datetime.now().strftime("%H:%M:%S"))
        else:
            print("Chatbot: Sorry, I don't understand that yet.")

# Run the chatbot
chatbot()






