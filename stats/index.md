---
layout: page
title: Probabilities & Statistics
---

{% for category in site.data.category-stats %}

<h2>{{ category.name }}</h2>
<u1>
    {% for topic in site.data.topic-stats %}
        {% assign topicCurr = site.stats | where: "name", topic.name %}
        {% for t in topicCurr %}
            {% if t.category == category.name %}
                <li class="nobull">
                    <a class="cleanLink" href="{{ t.url }}">{{ t.name }}</a>
                </li>
            {% endif %}
        {% endfor %}
    {% endfor %}
</u1>
{% endfor %}

<br>
<br>

<i>Sources:</i>
<br>
- <a href="http://www.editionstechnip.com/fr/catalogue-detail/149/probabilites-analyse-des-donnees-et-statistique.html">
    Probabilités, analyse des données et statistique</a>, Gilbert Saporta
<br>
- Télécom Paris courses
- Wikipedia