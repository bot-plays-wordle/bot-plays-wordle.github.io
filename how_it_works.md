---
layout: default
---
<a href="/">Back</a>

# How it works?

Let's take a look how the bot works internally and how it manages to solve the Wordle.

## Types of bots

Before we dive into details it worth mentioning that all bots can be splited into several categories. For simplicity let's call them **simple** and **advanced** bots.

Simple bots can do only very simple stuff. They do not know internals of the problem they are trying to solve, they don't learn on previous experience and so on.

On the other hand, advanced bots make use of more complex techniques like language processing, minimax search and maybe even machine learning.

## Key principles

At the time of writing the bot can be classified as **simple** bot. It uses a number of principles:
- words list
- letter frequency
- exclusion principle

Let's look into each of this principle separately

### Words list

Bot does not know anything about English words. It doesn't even know that it deals with English words.

All it has - huge list of possible words from which it can choose from.

There are multiple places where such work list can be found - you can easily google it. 

But for this bot the words list is taken from Unix system default location - `/usr/dict/words` (or `/usr/share/dict/words` on Mac). This words list is used by multiple applications and utilities including spellcheckers.

Basically preparation step requires filtering of this word list for 5 letter words and then excluding everything with special characters (like spaces and hypens).

This process gives us around 9000 words.

### Letter frequency

Next principle that should be taken into account is letter frequency. It's quite obvious that some letters have higher changes of appearing in the word than others. For example letter `E` will be more likely present in the word than letter `Q`.

There is a number of frequency tables available in the internet, for example [this](https://www3.nd.edu/~busiforc/handouts/cryptography/letterfrequencies.html).

### Exclusion principle

By exclusion principle we mean that we keep track which letters cannot be on particular spot of the word.

Initially all letters from `a` to `z` can be on every of 5 spots.

Now imagine that bot tries word `SMART` and gets the following feedback: **<span style="color: #6aaa64">S</span> <span>M A</span> <span style="color: #c9b458">R</span> <span>T</span>**

Having this information the bot can conclude that the only option for first letter is `S`.

Also bot can safely exclude `M`, `A` and `T` from **all** positions. Also `R` should be excluded as candidate for 4-th letter position.

## Choosing next word

Now let's examine how the bot chooses next guess.

In general bot keeps the following information:
- list of words that can be used (initially it has around 9000 words)
- letter candidates for each position (it will be later shrinked based on exclusion principle)
- known letters that are 100% present in the word

### Filtering words list

Before selecting a word bot needs to filter words list to exclude the words that cannot be the solution any more.

Let's look at previous example - **<span style="color: #6aaa64">S</span> <span>M A</span> <span style="color: #c9b458">R</span> <span>T</span>**

Based on this feedback the bot can safely exclude words like `GHOST` (`T` is not in the word), `BOARD` (`R` should be on a different spot) or `SOUND` (`R` should be in the word).

But `SUPER` is a potential candidate - it starts with `S` and has `R` somewhere int he word but not on 4-th position.

### Calculating word score

After words list is reduced it is time to choose best possible word.

For this purpose bot calculates the *score* of each word and chooses the one with highest score.

There are factors that contibute to the score:
- **letter frequency**. Words with more popular letters will yield higher score. This means that bot most likely choose the word with more popular letters
- **letter candidates** (based on exclusion principle). If bot sees that the word has only one option for some position it will take this word.
- **known letters**. The more known letters are in the word - the better
- **repeating letters** - words with different letters will have higher score as it might give better information about missing/present letters.

Intersing fact - with these rules in place the bot chooses `DRANT` as the opening word, despite words like `CRANE` or `LEARN` are considered as better options for the first word.

Also in general the bot tends to choose not so obvious (for a human) words - it's all due to how word's score is calculated.

## Is it optimal?

For sure, no!

A number of simulations were ran on a big data set of possible words (around 9000 words) and it average bot managed to find the correct word using `4.46` attempts. That seems like a good result, but there were a lot of occasions when it took more than 6 attempts to guess.

Here is the histogram for the simulation (in total 8496 games played):

| Attempts needed | Number of games |
|:----------------|:----------------|
| 1 | 1 |
| 2 | 153 |
| 3 | 1430 |
| 4 | 3214 |
| 5 | 2322 |
| 6 | 928 |
| 7 | 306 |
| 8 | 97 |
| 9 | 34 |
| 10 | 9 |
| 11 | 1 |
| 12 | 1 |

In general in 448 games (5.27%) more than 6 attempts were needed.

Surprisingly, some common words like `waste` were the ones where bot failed. In this case it took 8 attempts to guess. Main reason - there are *unpopular* letters inside the word.

Also the bot knows nothing about word structure. For example `s` and `t` often go joint together like `st`. Same for `s` and `h`. Often bot fails to make use of it.

So, there is a room for improvement for sure!