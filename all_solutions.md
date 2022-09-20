---
layout: sub-page
---
# All solutions

Here is a history of all solutions by month

{% assign prevGroup = "" %}
{% assign solutions = site.solutions | sort: 'date' | reverse %}
{% for solution in solutions %}
{% assign group = solution.date | date: "%B %Y" %}
{% if prevGroup != group %}
## {{ group }}
{% endif %}
{% assign prevGroup = group %}
<a href="{{ solution.url }}">{{ solution.title }}</a> - {% if solution.solved == true %}solved with <strong>{{ solution.attempts}}</strong> guesses{% else %}<strong>failed to solve</strong>{% endif %}. <a href="{{ solution.video_link }}">Video</a>
{% endfor %}