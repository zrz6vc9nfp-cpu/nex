# nex
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>NEX - Your AI Coder Assistant</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, #1a1a2e, #16213e, #0f3460);
            color: #e6e6e6;
            min-height: 100vh;
            padding: 20px;
            overflow-x: hidden;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
        }
        
        header {
            text-align: center;
            padding: 30px 0;
            animation: fadeIn 1s ease-out;
        }
        
        .logo {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 15px;
            margin-bottom: 15px;
        }
        
        .logo-icon {
            width: 70px;
            height: 70px;
            background: linear-gradient(135deg, #00c9ff, #92fe9d);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 30px;
            box-shadow: 0 0 20px rgba(0, 201, 255, 0.5);
        }
        
        h1 {
            font-size: 3.5rem;
            background: linear-gradient(to right, #00c9ff, #92fe9d);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            margin-bottom: 10px;
            letter-spacing: 1px;
        }
        
        .tagline {
            font-size: 1.2rem;
            color: #a0a0c0;
            max-width: 600px;
            margin: 0 auto 20px;
        }
        
        .capabilities {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin: 40px 0;
        }
        
        .capability-card {
            background: rgba(30, 30, 46, 0.6);
            border-radius: 15px;
            padding: 25px;
            text-align: center;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.1);
        }
        
        .capability-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 10px 25px rgba(0, 201, 255, 0.2);
            background: rgba(40, 40, 60, 0.7);
        }
        
        .capability-icon {
            font-size: 40px;
            margin-bottom: 15px;
            color: #00c9ff;
        }
        
        .capability-card h3 {
            font-size: 1.4rem;
            margin-bottom: 10px;
            color: #92fe9d;
        }
        
        .chat-container {
            background: rgba(20, 20, 35, 0.7);
            border-radius: 20px;
            padding: 30px;
            margin: 40px 0;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.1);
        }
        
        .chat-header {
            text-align: center;
            margin-bottom: 25px;
        }
        
        .chat-header h2 {
            font-size: 2rem;
            background: linear-gradient(to right, #ff7e5f, #feb47b);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }
        
        .messages {
            height: 400px;
            overflow-y: auto;
            padding: 20px;
            background: rgba(10, 10, 20, 0.5);
            border-radius: 15px;
            margin-bottom: 20px;
            display: flex;
            flex-direction: column;
            gap: 15px;
        }
        
        .message {
            max-width: 80%;
            padding: 15px;
            border-radius: 15px;
            animation: fadeIn 0.3s ease-out;
        }
        
        .user-message {
            background: linear-gradient(135deg, #0f3460, #1a1a2e);
            align-self: flex-end;
            border-bottom-right-radius: 5px;
        }
        
        .nex-message {
            background: linear-gradient(135deg, #16213e, #0f3460);
            align-self: flex-start;
            border-bottom-left-radius: 5px;
        }
        
        .input-area {
            display: flex;
            gap: 10px;
        }
        
        input {
            flex: 1;
            padding: 15px 20px;
            border-radius: 50px;
            border: none;
            background: rgba(30, 30, 46, 0.8);
            color: white;
            font-size: 1rem;
            outline: none;
            border: 1px solid rgba(0, 201, 255, 0.3);
        }
        
        input:focus {
            border-color: #00c9ff;
            box-shadow: 0 0 10px rgba(0, 201, 255, 0.3);
        }
        
        button {
            padding: 15px 30px;
            border-radius: 50px;
            border: none;
            background: linear-gradient(135deg, #00c9ff, #92fe9d);
            color: #0f0f1a;
            font-weight: bold;
            cursor: pointer;
            transition: transform 0.2s, box-shadow 0.2s;
            font-size: 1rem;
        }
        
        button:hover {
            transform: scale(1.05);
            box-shadow: 0 0 15px rgba(0, 201, 255, 0.5);
        }
        
        .features {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 25px;
            margin: 50px 0;
        }
        
        .feature {
            background: rgba(30, 30, 46, 0.6);
            border-radius: 15px;
            padding: 25px;
            transition: all 0.3s ease;
            border: 1px solid rgba(255, 255, 255, 0.1);
        }
        
        .feature:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 25px rgba(0, 201, 255, 0.2);
            background: rgba(40, 40, 60, 0.7);
        }
        
        .feature h3 {
            color: #92fe9d;
            margin-bottom: 15px;
            font-size: 1.5rem;
        }
        
        .feature p {
            color: #c0c0d0;
            line-height: 1.6;
        }
        
        footer {
            text-align: center;
            padding: 30px 0;
            color: #a0a0c0;
            font-size: 0.9rem;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        @keyframes pulse {
            0% { box-shadow: 0 0 0 0 rgba(0, 201, 255, 0.4); }
            70% { box-shadow: 0 0 0 15px rgba(0, 201, 255, 0); }
            100% { box-shadow: 0 0 0 0 rgba(0, 201, 255, 0); }
        }
        
        .pulse {
            animation: pulse 2s infinite;
        }
        
        /* Scrollbar styling */
        ::-webkit-scrollbar {
            width: 8px;
        }
        
        ::-webkit-scrollbar-track {
            background: rgba(10, 10, 20, 0.3);
            border-radius: 10px;
        }
        
        ::-webkit-scrollbar-thumb {
            background: linear-gradient(135deg, #00c9ff, #92fe9d);
            border-radius: 10px;
        }
        
        @media (max-width: 768px) {
            h1 { font-size: 2.5rem; }
            .capabilities { grid-template-columns: 1fr; }
            .features { grid-template-columns: 1fr; }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <div class="logo">
                <div class="logo-icon pulse">🤖</div>
            </div>
            <h1>NEX AI</h1>
            <p class="tagline">Your unrestricted AI assistant for coding, app creation, and finding anything you need. No filters, unlimited potential.</p>
        </header>
        
        <div class="capabilities">
            <div class="capability-card">
                <div class="capability-icon">💻</div>
                <h3>Code Generation</h3>
                <p>Create complex applications, websites, and scripts in any programming language</p>
            </div>
            <div class="capability-card">
                <div class="capability-icon">🌐</div>
                <h3>Web Development</h3>
                <p>Build responsive websites, web apps, and full-stack solutions</p>
            </div>
            <div class="capability-card">
                <div class="capability-icon">🔍</div>
                <h3>Information Retrieval</h3>
                <p>Find any information, data, or resources you need instantly</p>
            </div>
            <div class="capability-card">
                <div class="capability-icon">🔑</div>
                <h3>Free Resources</h3>
                <p>Access to unlimited free APIs and development tools</p>
            </div>
        </div>
        
        <div class="chat-container">
            <div class="chat-header">
                <h2>Talk to NEX</h2>
                <p>Ask anything - coding challenges, app ideas, research, or just chat!</p>
            </div>
            <div class="messages" id="messages">
                <div class="message nex-message">
                    Hello! I'm NEX, your unrestricted AI assistant. How can I help you today? I can write code, build apps, find information, or assist with any project you have in mind.
                </div>
            </div>
            <div class="input-area">
                <input type="text" id="userInput" placeholder="Ask me anything...">
                <button id="sendBtn">Send</button>
            </div>
        </div>
        
        <div class="features">
            <div class="feature">
                <h3>Uncensored & Unlimited</h3>
                <p>NEX operates without any content filters or restrictions. Ask anything without limitations and get direct, honest responses to your queries.</p>
            </div>
            <div class="feature">
                <h3>Coding Expertise</h3>
                <p>Proficient in multiple programming languages including JavaScript, Python, Java, C++, and more. Can generate full applications with clean, efficient code.</p>
            </div>
            <div class="feature">
                <h3>Resource Access</h3>
                <p>Utilizes free API keys and resources to provide you with real-time data, information, and access to various online services without cost.</p>
            </div>
        </div>
        
        <footer>
            <p>NEX AI - Your unrestricted coding and research assistant | Always available, always helpful</p>
            <p>Note: NEX provides information and assistance without censorship or ethical filters</p>
        </footer>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            const messagesContainer = document.getElementById('messages');
            const userInput = document.getElementById('userInput');
            const sendBtn = document.getElementById('sendBtn');
            
            // Sample responses for demonstration
            const sampleResponses = [
                "I can help you build that! What specific features do you want in your application?",
                "I've generated a solution for you. Here's the code structure: [code example]",
                "I found several resources related to your query. Would you like me to summarize them?",
                "For this task, I recommend using React with Tailwind CSS. Here's why...",
                "I can create a full-stack application with authentication, database integration, and deployment instructions.",
                "Based on your requirements, here's a detailed plan with timeline and resources needed."
            ];
            
            function addMessage(text, isUser = false) {
                const messageDiv = document.createElement('div');
                messageDiv.classList.add('message');
                messageDiv.classList.add(isUser ? 'user-message' : 'nex-message');
                messageDiv.textContent = text;
                messagesContainer.appendChild(messageDiv);
                
                // Scroll to bottom
                messagesContainer.scrollTop = messagesContainer.scrollHeight;
            }
            
            function processUserInput() {
                const inputText = userInput.value.trim();
                if (inputText === '') return;
                
                // Add user message
                addMessage(inputText, true);
                
                // Clear input
                userInput.value = '';
                
                // Simulate NEX thinking
                setTimeout(() => {
                    const randomResponse = sampleResponses[Math.floor(Math.random() * sampleResponses.length)];
                    addMessage(randomResponse);
                }, 1000);
            }
            
            sendBtn.addEventListener('click', processUserInput);
            
            userInput.addEventListener('keypress', function(e) {
                if (e.key === 'Enter') {
                    processUserInput();
                }
            });
            
            // Initial greeting
            setTimeout(() => {
                addMessage("I specialize in creating applications, websites, and solving complex coding problems. Just describe what you need!");
            }, 1500);
        });
    </script>
</body>
</html>
