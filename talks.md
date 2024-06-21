---
layout: default
---

# Talks
{% for person in site.workshop.talks %}
<div class="speaker">
    <h3 class="title" style="color:black">"Analysis of Pancreatic Tumors by Synthesis"<h3>
    <h3 class="name">Dr. {{ person.name }} {{ person.surname }}<h3>
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


