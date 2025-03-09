<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AI Chatbot</title>
    <style>
        body { font-family: Arial, sans-serif; }
        #chatbox { width: 300px; height: 400px; border: 1px solid #ccc; padding: 10px; overflow-y: auto; }
        #userInput { width: 80%; padding: 5px; }
        #sendBtn { padding: 5px; cursor: pointer; }
    </style>
</head>
<body>

    <h2>AI Chatbot</h2>
    <div id="chatbox"></div>
    <input type="text" id="userInput" placeholder="Type a message..." />
    <button id="sendBtn">Send</button>

    <script>
        async function sendMessage() {
            let userMessage = document.getElementById("userInput").value;
            if (!userMessage) return;

            document.getElementById("chatbox").innerHTML += "<p><b>You:</b> " + userMessage + "</p>";

            let response = await fetch("https://api.openai.com/v1/chat/completions", {
                method: "POST",
                headers: {
                    "Content-Type": "application/json",
                    "Authorization": "Bearer YOUR_OPENAI_API_KEY"
                },
                body: JSON.stringify({
                    model: "gpt-4",
                    messages: [{ role: "user", content: userMessage }]
                })
            });

            let data = await response.json();
            let botMessage = data.choices[0].message.content;

            document.getElementById("chatbox").innerHTML += "<p><b>Bot:</b> " + botMessage + "</p>";
            document.getElementById("userInput").value = "";
        }

        document.getElementById("sendBtn").addEventListener("click", sendMessage);
    </script>

</body>
</html>
