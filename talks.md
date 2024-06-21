---
layout: default
---

# Talks
{% for person in site.workshop.talks %}
<div class="speaker">
    <span class="title"> "Analysis of Pancreatic Tumors by Synthesis" <\span>
    <span class="name">Dr. {{ person.name }} {{ person.surname }}</span>
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


