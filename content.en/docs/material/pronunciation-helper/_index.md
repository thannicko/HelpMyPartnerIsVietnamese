---
title: "Pronunciation helper"
weight: 80
---

# Pronunciation helper

This tool is intended for you to be able to assemble different letters and hear their pronunciation in sequence. In doing this, you can deduce what the word is actually pronounced like.

<script type="text/javascript">
    var letters = []
    function addLetter(letterElement) {
        letters.push(letterElement.textContent);
        updateWord();
    }
    function clearAll() {
        letters = [];
        updateWord();
    }
    function removeLast() {
        letters.pop()
        updateWord()
    }
    function updateWord() {
        var word = ''
        for (const letter of letters) {
            word = word + letter
        }
        var wordElement = document.getElementById('word');
        wordElement.textContent = word;
    }
    function playAudio(audio){
        return new Promise(res=>{
            audio.play()
            audio.onended = res
        })
    }
    async function play(){
        for (const letter of letters) {
            var fileName = letter + '.wav';
            var audio = new Audio('audio/' + fileName);
            await playAudio(audio);
        }
    }
</script>


<p><b>Chosen word: </b><span id='word'></span></p>
<button onClick="play()">▶️</button>
<button onClick="clearAll()">❌</button>
<button onClick="removeLast()">🔙</button>

Click on the letters to assemble your word:

<button onClick="addLetter(this)">A</button>
<button onClick="addLetter(this)">B</button>