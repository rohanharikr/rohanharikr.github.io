---
layout: post
title: Rock, paper, scissors, javascript
<!-- description: What is the difference between various font formats?
summary: What is the difference between various font formats? -->
comments: true
tags: [javascript]
---

#### [Scroll down for full code.](#full-code)

#### Output

```
// Pass a choice as an argument to the main function.
You chose paper and computer chose rock.
You win!
```

#### Create an array of all possible choices   

```const choices = ["rock", "paper", "scissors"]```

#### Random Choice
This would give us a random number between 1 and the array length which in this case happens to be 3.

```Math.floor(Math.random() * choices.length)```


#### Main function
The ```Random Choice``` code is put inside a function because ideally, every time this function is called, a new choice would be generated.
```
function game(userChoice) {
    const computerChoice = choices[Math.floor(Math.random() * choices.length)]
    console.log(`You chose ${userChoice} and computer chose ${computerChoice}.`)

...}
 ```

#### Matchmaking
First things first, let's consider all the tie cases.

```
function game(userChoice) {
    const computerChoice = choices[Math.floor(Math.random() * choices.length)]
    console.log(`You chose ${userChoice} and computer chose ${computerChoice}.`)

   	if (userChoice === computerChoice) {
        console.log("It's a tie!")
    }

...}
```

#### All the cases when your choice is rock

```
if (userChoice === "rock") {
	if (computerChoice === "paper") {
            console.log("You lost!")
    } else if (computerChoice === "scissors") {
            console.log("You won!")
    }
```

#### Repeat for other n choices; this case, two

```
if (userChoice === "paper") {
    if (computerChoice === "rock") {
        console.log("You won!")
    } else if (computerChoice === "scissors") {
        console.log("You lost!")
    }
}

if (userChoice === "scissors") {
    if (computerChoice === "rock") {
        console.log("You lost!")
    } else if (computerChoice === "paper") {
        console.log("You won!")
    }
}
```

#### Optimise by writing all the cases in one block

```
if (userChoice === computerChoice) {
        console.log("It's a tie!")
    } else if (userChoice === "rock") {
        if (computerChoice === "paper") {
            console.log("You lost!")
        } else if (computerChoice === "scissors") {
            console.log("You won!")
        }
    } else if (userChoice === "paper") {
        if (computerChoice === "rock") {
            console.log("You won!")
        } else if (computerChoice === "scissors") {
            console.log("You lost!")
        }
    } else if (userChoice === "scissors") {
        if (computerChoice === "rock") {
            console.log("You lost!")
        } else if (computerChoice === "paper") {
            console.log("You won!")
        }
    }
```

#### <a name="full-code">Full Code</a>

<script src="https://gist.github.com/rohanharikr/8bfbd1471389e795b436cd87ab09a444.js"></script>