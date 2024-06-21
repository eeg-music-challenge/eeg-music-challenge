---
layout: default
---

# Talks
{% for person in site.workshop.talks %}
<div class="speaker">
    <div class="details" >
    <h3 class="name">Dr. {{ person.name }} {{ person.surname }}<h3>
    <h4 class="affiliation">{{ person.affiliation }}<h4>
    <span class="title">"Analysis of Pancreatic Tumors by Synthesis"<span>
        <div>
            <img src="{{ person.pic }}"/>
        </div>
        <div class="bio">
            <p>{{ person.bio }}</p>
        </div>
    </div>
</div>
{% endfor %}


