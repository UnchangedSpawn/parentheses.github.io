<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>English to Parentheses Translator</title>
    <style>
        body { font-family: Arial, sans-serif; text-align: center; margin: 50px; }
        textarea { width: 80%; height: 100px; margin: 10px 0; }
        button { padding: 10px 20px; font-size: 16px; cursor: pointer; }
        #output { font-size: 18px; margin-top: 20px; white-space: pre-wrap; word-wrap: break-word; }
    </style>
</head>
<body>

    <h2>English to Parentheses Translator</h2>
    <textarea id="inputText" placeholder="Type English text here..."></textarea><br>
    <button onclick="translateText()">Translate</button>
    <div id="output"></div>

    <script>
        function translateText() {
            let input = document.getElementById("inputText").value.toUpperCase();
            let output = "";

            for (let char of input) {
                if (char >= 'A' && char <= 'Z') {
                    let count = char.charCodeAt(0) - 65 + 1; // A = 1, B = 2, ..., Z = 26
                    output += "()" .repeat(count) + " ";
                } else if (char === " ") {
                    output += "  "; // Double space for readability
                }
            }

            document.getElementById("output").textContent = output;
        }
    </script>

</body>
</html>
