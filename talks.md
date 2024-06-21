---
layout: default
---

# Talks
{% for person in site.workshop.talks %}
<div class="speaker">
    <h2>Dr. {{ person.name }} {{ person.surname }}</h2>
    <span class="affiliation">{{ person.affiliation }}</span>
    <div class="details" >
        <div>
            <img src="{{ person.pic }}"/>
        </div>
        <div class="bio">
            <p>{{ person.bio }}</p>
        </div>
    </div>
</div>
{% endfor %}


