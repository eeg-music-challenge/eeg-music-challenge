---
layout: default
---

# Talks
{% for person in site.workshop.talks %}

<div class="speaker">
    <h2>Dr. {{ person.name }} {{ person.surname }}</h2>
    <span class="affiliation">{{ person.affiliation }}</span>
    <div class="details" style="display: flex; align-items: center; margin-top: 20px;">
        <div style="flex: 0 0 auto; margin-right: 20px; border-radius: 50%; width: 100px; height: 100px; overflow: hidden;">
            <img src="{{ person.pic }}" style="width: 100%; height: auto; border-radius: 50%;"/>
        </div>
        <div class="bio">
            <p>{{ person.bio }}</p>
        </div>
    </div>
</div>

{% endfor %}


