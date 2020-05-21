---
layout: page
title: Notes on machine learning
---

{% for category in site.data.category-ml %}

<h3>{{ category.name }}</h3>
<u1>
    {% for topic in site.data.topic-ml %}
        {% assign topicCurr = site.machinelearning | where: "name", topic.name %}
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

<i>Sources</i>:
<br>
- <a class="cleanLinkSource" href="https://www.cs.huji.ac.il/~shais/UnderstandingMachineLearning/understanding-machine-learning-theory-algorithms.pdf">
    Understanding Machine Learning: From Theory to Algorithms</a>, Shai Shalev-Shwartz and Shai Ben-David
<br>
- Télécom Paris courses
<br>
- <a class="cleanLinkSource" href="https://www.coursera.org/specializations/deep-learning">Deep learning classes</a>, Andrew Ng
<br>
- Wikipedia