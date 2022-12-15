---
layout: json
title: Statistics
permalink: /api/stats
---
<solutions>
  [
  {% for sol in site.solutions %}
    {
      "date": "{{ sol.date }}",
      "title": "{{ sol.title }}",
      "attempts": "{{ sol.attempts }}",
      "solved": "{{ sol.solved }}"
    }
    {% unless forloop.last %},{% endunless %}
  {% endfor %}
  ]
</solutions>