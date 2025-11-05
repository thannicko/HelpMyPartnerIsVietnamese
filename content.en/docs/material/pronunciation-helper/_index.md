---
title: "Pronunciation helper"
weight: 1
---

# Pronunciation helper

This tool is intended to help you get an idea how to pronounce any Vietnamese words. How does that work? In Vietnamese, a word's pronunciaton (or a very close approximation thereof) can be created by concatenating the sounds of all its letters. This tool will let you do exactly that.

{{< badge value="Example" >}} Tôi's pronunciation is obtained from "T" and "ôi".

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