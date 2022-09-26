---
layout: sub-page
---

# About

The idea of this project came to mind around early September 2022. As many of you I discovered [Wordle](https://www.nytimes.com/games/wordle/index.html) game. However for me it was quite late.

Basically I included Wordle into my morning routine.

## The challenge

However as non-native speaker I often struggled to find a word for my next attempt. Pretty soon I discovered [Word Hippo](https://www.wordhippo.com/what-is/word-finder-unscrambler.html) that helped to narrow down the possible words list.

Every time I was clueless I went to Word Hippo, typed in all letters I knew from my previous attempts, typed letters that should not be part of the word and checked the remaining list. It saved me in a number of games actually.

I was pretty happy with it, however the question I had was "can I do better?"

## Can I do better?

Next idea was to try and automate some of these steps.

I created a simple console application that used words list from my Mac (located at `/usr/share/dict/words`). Basically I typed in Wordle's response (equivalent of green, yellow and grey letters) into my application and it returned me a list of possible words.

During the next couple of days I came to a fully-functional bot that adviced which word to choose next. If you would like to know a bit more - check out [how it works](how_it_works.html) page.

But still it was a console application where I had to enter everything myself.

Same question appeared - "can I do better?"

## First steps to automation

As software engineer I had experience creating automated tests that used browser and emulated user interaction.

That was my next step to enhance the bot.

This time it opened a browser with Wordle game, used browser's API to type something, to check state of particular elements and all other stuff.

This way I got a bot that was autonomous - just run it and enjoy!

This resulted in [this repository on Github](https://github.com/sergeytrasko/wordle-solver). The code is there and you can use it as you want.

## More automation

Once I have a bot solving Wordle in a browser - can I record the screen? It turns out that yes, it's possible and quite easy to do.

But can I upload to Youtube? Also - yes, I can.

Can I generate the solution transcript based on what bot does? Yes, I can.

Can I add voiceover? Yes, I can.

These were the things I did in the next few weeks to enhance the bot.

## What I got in the end?

In the end (or is it the end really?) I've got a bot that can solve Wordle with quite high win rate (by the way it's quite close to mine).

Each night bot does the solve and publishes all artifacts to [Youtube](https://www.youtube.com/channel/UCHExvm1R3a7NFk5K89jUg7Q) channel and to this [site](https://www.botplayswordle.com).

All the processes are fully automated and every morning I have a fresh video I can use to compare my and bot's solutions.

## What's next?

Right now I see the project as almost complete. Few things I would like to imporve are around bot's logics. Some of bot's guesses are non-obvious and I somehow need to teach bot about common words.

All the rest seem to be working fine and I'm really happy with the results.

<!-- 
## But how it technically works?

Probably you are still wondering how it works internally? If so - please check out [technical details](tech_details) page. Hope you will get your answers there. 
-->

## Supporting the project

I don't plan to make money out of this project. It was made for fun. 

In total the whole project costed me $15 for the domain name plus my time to develop it during the evenings when everyone around is sleeping. That's why I don't have expectations about monetizing it.

However if you would like to support me - just buy bot a coffee:

<script type="text/javascript" src="https://cdnjs.buymeacoffee.com/1.0.0/button.prod.min.js" data-name="bmc-button" data-slug="sergeytrasko" data-color="#FFDD00" data-emoji=""  data-font="Cookie" data-text="Buy bot a coffee" data-outline-color="#000000" data-font-color="#000000" data-coffee-color="#ffffff" ></script>

If you want to contact me directly - just drop me a <a href="mailto:sergey.trasko@gmail.com?subject=Inquiry about 'Bot Plays Wordle'">mail</a>


