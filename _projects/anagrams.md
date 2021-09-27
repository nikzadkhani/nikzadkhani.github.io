---
layout: page
title: Anagrams Solver
description: A program to help you beat your friends at anagrams with python
img: /assets/img/anagrams.webp
redirect: https://github.com/nikzadkhani/Anagram-Solver
importance: 5
category: fun
---

<script type="text/javascript">
String.prototype.isAlpha = function() {
  var regExp = /^[A-Za-z]+$/;
  return (this.match(regExp));
};



function getDictionary(authToken){
    if(self.fetch){
        var setHeaders = new Headers();
        setHeaders.append('Authorization', 'Bearer ' + authToken.access_token);
        setHeaders.append('Content-Type', mime);

    var setOptions = {
        method: 'POST',
        headers: setHeaders
    };
    fetch(url,setOptions)
        .then(response => { if(response.ok){
        var reader = response.body.getReader();
        var decoder = new TextDecoder();
        reader.read().then(function(result){
            var data = {}
            data = decoder.decode(result.value, {stream: !result.done});
            console.log(data);
    });
        }
    else{
        console.log("Response wast not ok");
    }
  })  .catch(error => {
        console.log("There is an error " + error.message);
        });
    }
}
get_doc(dictionaryId, apiKey)

async function isWord(word) {
    let url = 'https://api.dictionaryapi.dev/api/v2/entries/en/' + word;
    let response = await fetch(url);
    let wordJson = await response.json()
    return wordJson.hasOwnProperty('word');
}

function findUniqueCharacters(characters) {
    var charList = characters.split("");
    var uniqueCharacters = new Array();
    charList.forEach((c) => {
        if (uniqueCharacters.indexOf(c) == -1) {
            uniqueCharacters.push(c)
        }
    })
    return uniqueCharacters
}


function permutator(inputArr) {
  var results = [];

  function permute(arr, memo) {
    var cur, memo = memo || [];

    for (var i = 0; i < arr.length; i++) {
      cur = arr.splice(i, 1);
      if (arr.length === 0) {
        results.push(memo.concat(cur));
      }
      permute(arr.slice(), memo.concat(cur));
      arr.splice(i, 0, cur[0]);
    }

    return results;
  }

  return permute(inputArr);
}

function getAnagrams(charList) {
    var permArr = [], usedChars = [];
    function permute(input) {
        var i, ch, chars = input.split("");
        for (i = 0; i < chars.length; i++) {
            ch = chars.splice(i, 1);
            usedChars.push(ch);
            if (chars.length == 0)
                var word = usedChars.join("");
                // if 
                // permArr[permArr.length] = 
            permute(chars.join(""));
            chars.splice(i, 0, ch);
            usedChars.pop();
        }
        return permArr
    }
    return permute(charList)
};


async function findAnagrams() {
    let userInput = document.getElementById('anagramLetters').value;
    let errorBox = document.getElementById("anagramError");
    if (userInput.length != 7) {
        errorBox.innerHTML = "Please input 7 characters";
        errorBox.hidden = false;
        return
    }
    if (!userInput.isAlpha()) {
        errorBox.innerHTML = "Please only include letters in the english alphabet.";
        errorBox.hidden = false;
        return
    }
    errorBox.hidden = true;
    let uniqueChars = findUniqueCharacters(userInput);
    console.log(getAnagrams(userInput))
}
</script>

DO this

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        <input class="anagram-input" maxlength='7' autocomplete='off' autocorrect='off' spellcheck='false' id="anagramLetters"/>
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        <button class="btn anagrams-btn" onclick="findAnagrams()">Run</button>
    </div>
</div>
<div class="alert alert-danger fade show" role="alert" id="anagramError" hidden>
Poo Poo
</div>
<br>
<br>
<div class="table-responsive anagrams-table">
<table class="table table-hover">
  <thead>
  <tr>
    <th>Company</th>
    <th>Contact</th> 
    <th>Country</th>
  </tr>
  </thead>
  <tbody>
  <tr>
    <td>Alfreds Futterkiste</td>
    <td>Maria Anders</td> 
    <td>Germany</td>
  </tr>
  <tr>
    <td>Centro comercial Moctezuma</td>
    <td>Francisco Chang</td> 
    <td>Mexico</td>
  </tr>
  </tbody>
</table>
</div>

Hello
