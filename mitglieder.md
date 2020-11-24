---
layout: default
title: Mitglieder
css: 
---
# Wer wir sind
{% assign SchSp = site.members | where: "position", "Schülersprecher" %}
{% assign VerLe = site.members | where: "position", "Verbindungslehrer" %}
{% assign Mem = site.members | where: "position", "Mitglied" %}
## Schülersprecher
{% for member in SchSp %}
<div class="memberCard">
    {% capture imgUrl %}/assets/images/members/{{member.image}}{% endcapture %}
    <img src="{{ imgUrl | relative_url }}" style="height: 100px;">
    <span>
    <p><b>{{member.name}}</b></p>
    {{ member.content }}
    </span>
</div>
{% endfor %}
## Verbindungslehrer
{% for member in VerLe %}
<div class="memberCard">
    {% capture imgUrl %}/assets/images/members/{{member.image}}{% endcapture %}
    <img src="{{ imgUrl | relative_url }}" style="height: 100px;">
    <span>
    <p><b>{{member.name}}</b></p>
    {{ member.content }}
    </span>
</div>
{% endfor %}
## Mitglieder
{% for member in Mem %}
<div class="memberCard">
    {% capture imgUrl %}/assets/images/members/{{member.image}}{% endcapture %}
    <img src="{{ imgUrl | relative_url }}" style="height: 100px;">
    <span>
    <p><b>{{member.name}}</b></p>
    {{ member.content }}
    </span>
</div>
{% endfor %}
