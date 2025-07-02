<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Happy Birthday!</title>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;700&display=swap" rel="stylesheet">
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        /* Custom styles for a festive look */
        body {
            font-family: 'Inter', sans-serif;
            background: linear-gradient(135deg, #fce4ec 0%, #e0f2f7 100%); /* Soft gradient background */
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh; /* Full viewport height */
            margin: 0;
            overflow: hidden; /* Hide overflow from confetti */
        }
        .card-container {
            background-color: #ffffff;
            padding: 2.5rem;
            border-radius: 1.5rem; /* More rounded corners */
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.15); /* Stronger shadow */
            text-align: center;
            max-width: 600px;
            width: 90%; /* Responsive width */
            position: relative;
            z-index: 10; /* Ensure card is above confetti */
            animation: fadeInScale 1s ease-out forwards;
        }
        @keyframes fadeInScale {
            from {
                opacity: 0;
                transform: scale(0.9);
            }
            to {
                opacity: 1;
                transform: scale(1);
            }
        }
        .header-text {
            color: #e91e63; /* Pink for main heading */
            font-size: 3rem;
            font-weight: 700;
            margin-bottom: 1.5rem;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.1);
        }
        .message-text {
            color: #333333;
            font-size: 1.25rem;
            line-height: 1.8;
            margin-bottom: 2rem;
        }
        .signature-text {
            color: #666666;
            font-size: 1rem;
            font-style: italic;
            margin-top: 2rem;
        }
        .confetti {
            position: absolute;
            width: 10px;
            height: 10px;
            background-color: #ffeb3b; /* Yellow */
            border-radius: 50%;
            opacity: 0;
            animation: confettiFall 5s infinite;
        }
        .confetti:nth-child(2n) { background-color: #4fc3f7; /* Blue */ }
        .confetti:nth-child(3n) { background-color: #8bc34a; /* Green */ }
        .confetti:nth-child(4n) { background-color: #ff9800; /* Orange */ }
        .confetti:nth-child(5n) { background-color: #e91e63; /* Pink */ }

        /* Confetti animation */
        @keyframes confettiFall {
            0% {
                transform: translateY(-100px) rotate(0deg);
                opacity: 0;
            }
            10% {
                opacity: 1;
            }
            100% {
                transform: translateY(100vh) rotate(720deg);
                opacity: 0;
            }
        }

        /* Styles for the Gemini API integration */
        .gemini-section {
            margin-top: 2.5rem;
            padding-top: 1.5rem;
            border-top: 1px solid #e0e0e0;
            text-align: left; /* Align text within this section to left */
        }
        .gemini-section label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: 600;
            color: #333;
        }
        .gemini-section textarea {
            width: 100%;
            padding: 0.75rem;
            border: 1px solid #ccc;
            border-radius: 0.5rem;
            min-height: 80px;
            resize: vertical;
            font-size: 1rem;
        }
        .gemini-section button {
            background: linear-gradient(45deg, #f06292, #e91e63); /* Pink gradient button */
            color: white;
            padding: 0.75rem 1.5rem;
            border: none;
            border-radius: 0.75rem;
            font-size: 1.1rem;
            font-weight: 700;
            cursor: pointer;
            margin-top: 1rem;
            transition: transform 0.2s ease, box-shadow 0.2s ease;
            box-shadow: 0 4px 10px rgba(233, 30, 99, 0.3);
        }
        .gemini-section button:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 15px rgba(233, 30, 99, 0.4);
        }
        .generated-message {
            margin-top: 1.5rem;
            padding: 1rem;
            background-color: #f9f9f9;
            border: 1px dashed #e91e63;
            border-radius: 0.75rem;
            font-style: italic;
            color: #555;
            min-height: 50px;
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center; /* Center the generated text */
        }
        .loading-indicator {
            display: none; /* Hidden by default */
            margin-top: 1rem;
            font-style: italic;
            color: #e91e63;
        }
    </style>
</head>
<body>
    <!-- Confetti elements (purely decorative CSS animation) -->
    <div class="confetti" style="left: 10%; animation-delay: 0s;"></div>
    <div class="confetti" style="left: 20%; animation-delay: 1s; width: 8px; height: 8px;"></div>
    <div class="confetti" style="left: 30%; animation-delay: 0.5s;"></div>
    <div class="confetti" style="left: 40%; animation-delay: 2s; width: 12px; height: 12px;"></div>
    <div class="confetti" style="left: 50%; animation-delay: 1.5s;"></div>
    <div class="confetti" style="left: 60%; animation-delay: 2.5s; width: 7px; height: 7px;"></div>
    <div class="confetti" style="left: 70%; animation-delay: 0.8s;"></div>
    <div class="confetti" style="left: 80%; animation-delay: 3s;"></div>
    <div class="confetti" style="left: 90%; animation-delay: 1.2s; width: 9px; height: 9px;"></div>
    <div class="confetti" style="left: 15%; animation-delay: 3.5s;"></div>
    <div class="confetti" style="left: 25%; animation-delay: 0.3s; width: 11px; height: 11px;"></div>
    <div class="confetti" style="left: 35%; animation-delay: 2.2s;"></div>
    <div class="confetti" style="left: 45%; animation-delay: 0.7s;"></div>
    <div class="confetti" style="left: 55%; animation-delay: 1.8s; width: 6px; height: 6px;"></div>
    <div class="confetti" style="left: 65%; animation-delay: 2.8s;"></div>
    <div class="confetti" style="left: 75%; animation-delay: 1.1s;"></div>
    <div class="confetti" style="left: 85%; animation-delay: 0.6s; width: 10px; height: 10px;"></div>

    <div class="card-container">
        <h1 class="header-text">🥳 Happy Birthday, Siva Krishna 🎂</h1>
        <p class="message-text" id="default-message">
            Wishing you a day filled with joy, laughter, and all the things that make you happy!
            May your year ahead be even brighter than the last, full of exciting adventures,
            wonderful memories, and success in everything you do.
            <br><br>
            You are an amazing person, and we hope you have the most fantastic birthday ever!
        </p>
        <p class="signature-text">With love and best wishes,<br> [Your Name/Group Name]</p>

        <!-- Gemini API Integration Section -->
        <div class="gemini-section">
            <label for="birthdayPersonDesc">✨ Get a Personalized Message! ✨</label>
            <textarea id="birthdayPersonDesc" placeholder="Tell me about the birthday person (e.g., 'my best friend who loves hiking and cats', 'my dad who is a great cook and loves history'). Also, mention your relationship to them."></textarea>
            <button id="generateMessageBtn">✨ Generate Message ✨</button>
            <div id="loadingIndicator" class="loading-indicator">Generating your message...</div>
            <div id="generatedMessageOutput" class="generated-message">Your personalized message will appear here!</div>
        </div>
    </div>

    <script>
        document.getElementById('generateMessageBtn').addEventListener('click', async () => {
            const description = document.getElementById('birthdayPersonDesc').value;
            const generatedMessageOutput = document.getElementById('generatedMessageOutput');
            const loadingIndicator = document.getElementById('loadingIndicator');
            const defaultMessage = document.getElementById('default-message');

            if (!description.trim()) {
                generatedMessageOutput.textContent = "Please provide some description to generate a message.";
                return;
            }

            loadingIndicator.style.display = 'block'; // Show loading indicator
            generatedMessageOutput.textContent = ''; // Clear previous message
            defaultMessage.style.display = 'none'; // Hide default message when generating

            const prompt = `Generate a personalized birthday wish for someone based on the following description: "${description}". Keep it warm, friendly, and suitable for a general audience. The message should be around 50-70 words.`;

            let chatHistory = [];
            chatHistory.push({ role: "user", parts: [{ text: prompt }] });

            const payload = { contents: chatHistory };
            const apiKey = ""; // Leave this as-is; Canvas will provide the key
            const apiUrl = `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.0-flash:generateContent?key=${apiKey}`;

            try {
                const response = await fetch(apiUrl, {
                    method: 'POST',
                    headers: { 'Content-Type': 'application/json' },
                    body: JSON.stringify(payload)
                });

                const result = await response.json();

                if (result.candidates && result.candidates.length > 0 &&
                    result.candidates[0].content && result.candidates[0].content.parts &&
                    result.candidates[0].content.parts.length > 0) {
                    const text = result.candidates[0].content.parts[0].text;
                    generatedMessageOutput.textContent = text;
                } else {
                    generatedMessageOutput.textContent = "Could not generate a message. Please try again.";
                }
            } catch (error) {
                console.error('Error calling Gemini API:', error);
                generatedMessageOutput.textContent = "An error occurred while generating the message. Please try again.";
            } finally {
                loadingIndicator.style.display = 'none'; // Hide loading indicator
            }
        });
    </script>
</body>
</html>
