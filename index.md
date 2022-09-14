---
layout: default
---

# Welcome

Welcome to **Bot Plays Wordle**!

Have you ever played [Wordle](https://www.nytimes.com/games/wordle/index.html)? If not - you should try it out!

On this site a bot is playing Wordle game and tries to guess daily word.

## Videos and Recordings 

All the videos are available on [Youtube](https://www.youtube.com/channel/UCHExvm1R3a7NFk5K89jUg7Q) channel - like and subscribe for daily updates.

<div class="g-ytsubscribe" data-channelid="UCHExvm1R3a7NFk5K89jUg7Q" data-layout="full" data-count="default"></div>

## Breakdowns

Also you can refer to breakdowns of previous days solutions:

{% assign solutions = site.solutions | sort: 'date' | reverse %}
{% for solution in solutions %}
<a href="{{ solution.url }}">{{ solution.title }}</a>
{% endfor %}

## Statistics

Will be published layer once there is more data - stay tuned!