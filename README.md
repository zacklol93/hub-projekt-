<!DOCTYPE html>
<html lang="pl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Wyszukiwarka Palindromów</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #000000;
            display: flex;
            flex-direction: column;
            align-items: center;
            padding: 20px;
            color: #ffffff; 
        }

        h1 { color: #ff0000; }

        .container {
            display: flex;
            gap: 20px;
            width: 100%;
            max-width: 1200px;
            height: 500px;
        }

        .box {
            flex: 1;
            display: flex;
            flex-direction: column;
        }

        label {
            margin-bottom: 10px;
            font-weight: bold;
            color: #ff0000;
        }

        textarea, #output {
            flex: 1;
            padding: 15px;
            border: 2px solid #ff3c00;
            border-radius: 8px;
            font-size: 16px;
            line-height: 1.6;
            background-color: rgb(0, 0, 0);
            color: #ffffff;
            overflow-y: auto;
            white-space: pre-wrap;
            word-wrap: break-word;
        }

        textarea {
            resize: none;
            outline: none;
            transition: border-color 0.3s;
        }

        textarea:focus {
            border-color: #ff0000;
        }

        .palindrome {
            background-color: #ff0000;
            color: #ffffff;
            border-bottom: 2px solid #d35400;
            border-radius: 3px;
            font-weight: bold;
            padding: 0 2px;
        }
    </style>
</head>
<body>

    <h1>Wyszukiwarka Palindromów</h1>
    
    <div class="container">
        <div class="box">
            <label for="input-text">Wklej tekst:</label>
            <textarea id="input-text" placeholder="Np. Kamil ślimak, Kobyła ma mały bok..."></textarea>
        </div>

        <div class="box">
            <label>Odbiór:</label>
            <div id="output"></div>
        </div>
    </div>

    <script src="script.js"></script>
</body>
</html>
--------------------
const input = document.getElementById('input-text');
const output = document.getElementById('output');

input.addEventListener('input', () => {
    const text = input.value;
    if (!text) {
        output.innerHTML = "";
        return;
    }

    /**
     * Czyści tekst, zostawiając tylko małe litery i cyfry.
     * Obsługuje polskie znaki diakrytyczne.
     */
    function getCleaned(str) {
        return str.toLowerCase().replace(/[^a-z0-9ąęćłńóśźż]/gi, '');
    }

    /**
     * Sprawdza, czy dana fraza jest palindromem.
     * Ignoruje wielkość liter, spacje i znaki interpunkcyjne.
     */
    function isPalindrome(str) {
        const cleaned = getCleaned(str);
        if (cleaned.length < 3) return false; 
        return cleaned === cleaned.split('').reverse().join('');
    }

    // Rozbicie tekstu na "atomy" (słowa, spacje, znaki interpunkcyjne)
    // Dzięki temu zachowujemy oryginalny wygląd tekstu w oknie wyjściowym
    const tokens = text.match(/([a-z0-9ąęćłńóśźż]+|[^a-z0-9ąęćłńóśźż])/gi) || [];
    
    let resultHTML = "";
    let i = 0;

    // Algorytm okna przesuwnego (szuka najdłuższego palindromu od danego miejsca)
    while (i < tokens.length) {
        let foundLongest = false;

        for (let j = tokens.length; j > i; j--) {
            const currentPhrase = tokens.slice(i, j).join('');
            
            if (isPalindrome(currentPhrase)) {
                resultHTML += `<span class="palindrome">${currentPhrase}</span>`;
                i = j; // Przeskok do końca znalezionego palindromu
                foundLongest = true;
                break;
            }
        }

        if (!foundLongest) {
            resultHTML += tokens[i];
            i++;
        }
    }

    output.innerHTML = resultHTML;
});
