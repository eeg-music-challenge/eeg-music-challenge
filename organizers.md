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

# Program Committee

{% for person in site.workshop.pc %}
* {{ person.name }} {{ person.surname }} ({{person.affiliation }})
{% endfor %}
* ...more coming
<!-- Coming soon...-->

# Contact

Click on your favorite organizer to contact us for any additional information!
