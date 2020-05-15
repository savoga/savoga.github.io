---
layout: page
title: Machine Learning
---

{% for category in site.data.category-ml %}

<p>{{ category.name }}</p>
<u1>
    {% for topic in site.data.topic-ml %}
        {% assign topicCurr = site.machinelearning | where: "name", topic.name %}
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

Sources:
<br>
- <a href="https://www.cs.huji.ac.il/~shais/UnderstandingMachineLearning/understanding-machine-learning-theory-algorithms.pdf">
    Understanding Machine Learning: From Theory to Algorithms</a>, Shai Shalev-Shwartz and Shai Ben-David
<br>
- Télécom Paris courses
<br>
- <a href="https://www.coursera.org/specializations/deep-learning">Deep learning classes</a>, Andrew Ng
<br>
- Wikipedia