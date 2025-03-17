---
layout: post 
title: Teach
search_exclude: true
permalink: /teach/lists_and_filtering_algorithms
---
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Interactive Lesson: Lists & Filtering Algorithms</title>
    <style>
        body {
            font-family: 'Poppins', sans-serif;
            margin: 0;
            padding: 0;
            background: linear-gradient(120deg, #1e1e1e, #3a3a3a);
            color: white;
            text-align: center;
        }
        .container {
            max-width: 800px;
            margin: 50px auto;
            padding: 30px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 15px;
            box-shadow: 0px 5px 15px rgba(0, 0, 0, 0.3);
        }
        .code-box {
            background: #111;
            padding: 15px;
            border-radius: 8px;
            font-family: monospace;
            text-align: left;
            overflow-x: auto;
        }
        .hidden {
            display: none;
        }
        button {
            padding: 12px 20px;
            background: #ff6b6b;
            color: white;
            border: none;
            cursor: pointer;
            border-radius: 5px;
            margin-top: 15px;
            font-size: 16px;
            transition: 0.3s;
        }
        button:hover {
            background: #ff3b3b;
        }
        .practice-area {
            margin-top: 30px;
            padding: 20px;
            background: rgba(255, 255, 255, 0.15);
            border-radius: 10px;
        }
        input, select {
            padding: 10px;
            margin: 10px;
            border-radius: 5px;
            border: none;
            font-size: 16px;
        }
        .interactive-output {
            margin-top: 20px;
            font-weight: bold;
            color: #ffcc00;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>🔹 Interactive Lesson: Lists & Filtering Algorithms 🔹</h1>
        <p>Welcome to an exciting lesson on Lists & Filtering Algorithms! This lesson is designed for beginners, so even if you've never coded before, you'll get it! 🚀</p>
        <h2>📌 What is a List?</h2>
        <p>A <b>list</b> is a collection of items stored in an ordered way. Think of it like a shopping list, where each item has a position.</p>
        <div class="code-box">
            <code>
                # Example of a Python List
                fruits = ["apple", "banana", "cherry", "date"]
                print(fruits[0])  # Output: apple
            </code>
        </div>
        <h2>🔍 Filtering a List</h2>
        <p>Filtering helps us pick specific items based on a condition. Imagine filtering out only the ripe fruits from a basket!</p>
        <div class="code-box">
            <code>
                numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
                even_numbers = list(filter(lambda x: x % 2 == 0, numbers))
                print(even_numbers)
            </code>
        </div>
        <button onclick="document.getElementById('answer1').classList.toggle('hidden')">Reveal Answer</button>
        <p id="answer1" class="hidden">Answer: [2, 4, 6, 8, 10]</p>
        <h2>🤔 Interactive Practice</h2>
        <div class="practice-area">
            <p>Try filtering words with more than <b>4 letters</b>!</p>
            <input type="text" id="wordInput" placeholder="Enter words separated by commas">
            <button onclick="filterWords()">Filter!</button>
            <p class="interactive-output" id="output"></p>
        </div>
        <h2>🧠 Challenge: Removing Duplicates</h2>
        <p>Can you remove duplicates from the following list?</p>
        <div class="code-box">
            <code>
                numbers = [5, 2, 8, 5, 10, 8, 3]
                unique_numbers = list(set(numbers))
                print(unique_numbers)
            </code>
        </div>
        <button onclick="document.getElementById('answer2').classList.toggle('hidden')">Reveal Answer</button>
        <p id="answer2" class="hidden">Answer: [2, 3, 5, 8, 10]</p>
        <h2>🌟 Creative Development: Design Your Own Filter</h2>
        <p>Now, it's your turn! Design a filter that extracts words starting with a vowel from a list. Here's a starting point:</p>
        <div class="code-box">
            <code>
                words = ["apple", "banana", "orange", "grape", "umbrella"]
                vowels = ['a', 'e', 'i', 'o', 'u']
                vowel_words = [word for word in words if word[0].lower() in vowels]
                print(vowel_words)
            </code>
        </div>
        <button onclick="document.getElementById('answer3').classList.toggle('hidden')">Reveal Answer</button>
        <p id="answer3" class="hidden">Answer: ['apple', 'orange', 'umbrella']</p>
        <h2>💬 Discussion: Impact of Filtering Algorithms</h2>
        <p>Filtering algorithms are everywhere! They help search engines find relevant results and email services filter out spam. However, they can also create "filter bubbles," limiting the information we see. Let's discuss the ethical implications of filtering algorithms.</p>
        <script>
            function filterWords() {
                let input = document.getElementById('wordInput').value;
                let words = input.split(',').map(word => word.trim());
                let filteredWords = words.filter(word => word.length > 4);
                document.getElementById('output').innerText = `Filtered Words: ${filteredWords.join(', ')}`;
            }
        </script>
    </div>
</body>
</html>