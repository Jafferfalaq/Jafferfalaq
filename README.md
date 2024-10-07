<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Jaffer - AI Chatbot</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            padding: 20px;
        }
        #chatbox {
            border: 1px solid #ccc;
            height: 300px;
            overflow-y: scroll;
            padding: 10px;
            background: white;
        }
        .user-message {
            text-align: right;
            margin: 5px;
            color: blue;
        }
        .bot-message {
            text-align: left;
            margin: 5px;
            color: green;
        }
        input[type="text"] {
            width: calc(100% - 22px);
            padding: 10px;
        }
    </style>
</head>
<body>
    <h1>Jaffer - AI Chatbot</h1>
    <div id="chatbox"></div>
    <input type="text" id="userInput" placeholder="Type your message..." />
    <button id="sendBtn">Send</button>

    <script>
        const chatbox = document.getElementById('chatbox');
        const userInput = document.getElementById('userInput');
        const sendBtn = document.getElementById('sendBtn');

        function addMessage(message, className) {
            const messageElement = document.createElement('div');
            messageElement.textContent = message;
            messageElement.className = className;
            chatbox.appendChild(messageElement);
            chatbox.scrollTop = chatbox.scrollHeight; // Scroll to the bottom
        }

        function getBotResponse(userMessage) {
            // Simple AI response logic
            if (userMessage.includes('hello') || userMessage.includes('hi')) {
                return "Hello! I'm Jaffer, your AI assistant.";
            } else if (userMessage.includes('how are you')) {
                return "I'm just a program, but thanks for asking!";
            } else {
                return "I'm not sure how to respond to that.";
            }
        }

        sendBtn.addEventListener('click', function() {
            const userMessage = userInput.value;
            if (userMessage.trim() !== "") {
                addMessage(userMessage, 'user-message');
                userInput.value = ''; // Clear input field

                const botResponse = getBotResponse(userMessage);
                addMessage(botResponse, 'bot-message');
            }
        });

        // Optional: Send message on Enter key press
        userInput.addEventListener('keypress', function(event) {
            if (event.key === 'Enter') {
                sendBtn.click();
            }
        });
    </script>
</body>
</html>
