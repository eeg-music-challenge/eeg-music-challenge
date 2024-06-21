---
layout: default
---

# Talks
{% for person in site.workshop.talks %}
<!-- <div class="speaker">
    <div class="details" >
    <h2 class="name">Dr. {{ person.name }} {{ person.surname }}<h2>
    <h2 class="affiliation">{{ person.affiliation }}<h2>
    <h3 class="title">"Analysis of Pancreatic Tumors by Synthesis"<h3>
        <div>
            <img src="{{ person.pic }}"/>
        </div>
        <div class="bio">
            <p>{{ person.bio }}</p>
        </div>
    </div>
</div>-->
<div class="speaker">
    <div class="cont">
        <span class="title">Title of the talk: {{ person.title }}</span>
        <img src="{{ person.pic }}"/>
        <div class="details">
            <span class="name">{{ person.name }}<br>{{ person.surname }}</span>
            <span class="affiliation">{{ person.affiliation }}</span>
            <!-- <span class="affiliation"><a href='{{ person.file_url }}'>{{ person.file_text }}</a></span>--> 
            <span class="bio">{{ person.bio }}<span>
        </div>
    </div>
</div>
{% endfor %}


