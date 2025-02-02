<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>English & Parentheses Translator</title>
    <style>
        body { font-family: Arial, sans-serif; text-align: center; margin: 50px; }
        textarea { width: 80%; height: 100px; margin: 10px 0; }
        button { padding: 10px 20px; font-size: 16px; cursor: pointer; margin: 5px; }
        #output { font-size: 18px; margin-top: 20px; white-space: pre-wrap; word-wrap: break-word; }
    </style>
</head>
<body>

    <h2>English ↔ Parentheses Translator</h2>
    
    <textarea id="inputText" placeholder="Enter English or Parentheses..."></textarea><br>
    
    <button onclick="translateToParentheses()">Translate to Parentheses</button>
    <button onclick="translateToEnglish()">Translate to English</button>

    <div id="output"></div>

    <script>
        function translateToParentheses() {
            let input = document.getElementById("inputText").value.toUpperCase();
            let output = "";

            for (let char of input) {
                if (char >= 'A' && char <= 'Z') {
                    let count = char.charCodeAt(0) - 65 + 1; // A = 1, B = 2, ..., Z = 26
                    output += "()".repeat(count) + " ";
                } else if (char === " ") {
                    output += "  "; // Double space for readability
                }
            }

            document.getElementById("output").textContent = output.trim();
        }

        function translateToEnglish() {
            let input = document.getElementById("inputText").value.trim();
            let groups = input.split(/\s+/); // Split by spaces
            let output = "";

            for (let group of groups) {
                let count = (group.match(//g) || []).length; // Count occurrences of "()"
                if (count > 0 && count <= 26) {
                    output += String.fromCharCode(64 + count); // Convert count to A-Z
                } else {
                    output += " "; // Keep spaces
                }
            }

            document.getElementById("output").textContent = output;
        }
    </script>

</body>
</html>
