---
layout: page
title: People
permalink: /people/
---

{% assign people_sorted = site.people | sort: "joined" %}
{% assign role_array = "pi|postdoc|phd|researchstaff|visiting|others|alumni" | split: "|" %}

{% for role in role_array %}
  {% assign people_in_role = people_sorted | where: "position", role %}
  {% if people_in_role.size > 0 %}

    <div class="pos_header">
      {% case role %}
        {% when "pi" %}            <h3>Principal Investigator</h3>
        {% when "postdoc" %}      <h3>Postdoctoral Fellows</h3>
        {% when "phd" %}          <h3>Graduate Students</h3>
        {% when "researchstaff" %}<h3>Research Staff</h3>
        {% when "visiting" %}     <h3>Visiting Scholars</h3>
        {% when "others" %}       <h3>Honorary Members</h3>
        {% when "alumni" %}       <h3>Alumni</h3>
      {% endcase %}
    </div>

    {% if role != "alumni" %}
      <div class="content list people">
        {% for profile in people_in_role %}
          <div class="list-item-people">
            <p class="list-post-title">
              {% if profile.avatar %}
                <a href="{{ profile.url | relative_url }}">
                  <img class="profile-thumbnail"
                       src="{{ "/images/people/" | append: profile.avatar | relative_url }}"
                       alt="{{ profile.name }}">
                </a>
              {% else %}
                <a href="{{ profile.url | relative_url }}">
                  <img class="profile-thumbnail"
                       src="https://your.default/avatar.jpg"
                       alt="{{ profile.name }}">
                </a>
              {% endif %}
              <a class="name" href="{{ profile.url | relative_url }}">{{ profile.name }}</a>
            </p>
          </div>
        {% endfor %}
      </div>
      <hr>
      
  {% else %}
    <br>
    | Who are they | When were they here | Where they went |
    | :------------- |:-------------| :-----------|
    | [Tony Liu](...) | Graduate Student (2018-2024) | Assistant Prof... |
    <!-- ... -->
  {% endif %}
{% endfor %}

