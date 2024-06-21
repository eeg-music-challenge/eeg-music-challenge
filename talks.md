---
layout: default
---

# Talks


{% for person in site.workshop.talks %}
<div class="speaker">
    <div class="cont">
        <div class="details">
            <img src="{{ person.pic }}"/>
            <span class="name">{{ person.name }}<br>{{ person.surname }}</span>
            <span class="affiliation">{{ person.affiliation }}</span>
            <span class="title">Title of the talk: {{ person.title }} </span>
            <span class="bio"> {{ person.bio }} <\span>
            <!-- <span class="affiliation"><a href='{{ person.file_url }}'>{{ person.file_text }}</a></span>-->
        </div>
    </div>
</div>
{% endfor %}
