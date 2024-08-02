---
layout: default
---

# Organizers

<p>
{% for person in site.workshop.organizers %}
<a href="mailto:{{ person.email }}">
<div class="item">
    <img class="headshot" src="{{ person.pic }}"/>
    <span class="name">{{ person.name }}<br>{{ person.surname }}</span>
    <span class="affiliation">{{ person.affiliation }}</span>
</div>
</a>
{% endfor %}
</p>

# Contact

Content
