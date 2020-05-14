---
layout: page
title: Stats
excerpt: "stats page"
---

<h1>Probabilities and Statistics</h1>

{% for category in site.data.category-stats %}

<p>{{ category.name }}</p>
<u1>
    {% for topic in site.data.topic-stats %}
        {% assign topicCurr = site.stats | where: "name", topic.name %}
        {% for t in topicCurr %}
            {% if t.category == category.name %}
                <li>
                    <a href="{{ t.url }}">{{ t.name }}</a>
                </li>
            {% endif %}
        {% endfor %}
    {% endfor %}
</u1>
{% endfor %}