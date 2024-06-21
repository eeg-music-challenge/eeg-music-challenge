---
layout: default
---

# Talks


{% for person in site.workshop.talks %}
<div class="speaker">
    <div class="cont">
        <h2>Dr. {{ person.name }}<br>{{ person.surname }}</h2>
        <div class="details">
            <!--img src="{{ person.pic }}"/>-->
            <!-- <span class="name">{{ person.name }}<br>{{ person.surname }}</span> -->
            <!-- <span class="affiliation">{{ person.affiliation }}</span>-->
            <!-- <span class="title">Title of the talk: <!-- {{ person.title }} --></span>-->
            <!-- <span class="affiliation"><a href='{{ person.file_url }}'>{{ person.file_text }}</a></span>-->
            <div class="image-container">
                <img src="{{ person.pic }}" style="border-radius: 50%;"/>
            </div>
            <div class="bio">
                <p>{{ person.bio }}</p> <!-- Assuming 'person.bio' is where the biography is stored -->
            </div>
        </div>
    </div>
</div>
{% endfor %}
