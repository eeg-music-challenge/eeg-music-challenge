---
layout: default
---

# Talks

<style>
    .speaker .details {
        display: flex;
        align-items: center;
        margin-top: 20px;
    }

    .speaker .details .image-container {
        flex: 0 0 auto;
        margin-right: 20px;
        border-radius: 50%;
        width: 100px;
        height: 100px;
        overflow: hidden;
    }

    .speaker .details img {
        width: 100%;
        height: auto;
        border-radius: 50%;
    }

    .speaker .bio {
        flex: 1;
    }
</style>

{% for person in site.workshop.talks %}
<!-- <div class="speaker">
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
</div>-->
<div class="speaker">
    <h2>Dr. {{ person.name }} {{ person.surname }}</h2>
    <span class="affiliation">{{ person.affiliation }}</span>
    <div class="details" style="display: flex; align-items: center; margin-top: 20px;">
        <div style="flex: 0 0 auto; margin-right: 20px; border-radius: 50%; width: 100px; height: 100px; overflow: hidden;">
            <img src="{{ person.pic }}" style="width: 100%; height: auto; border-radius: 50%;"/>
        </div>
        <div class="bio">
            <p>Biography or other relevant text goes here.</p>
        </div>
    </div>
</div>

{% endfor %}


