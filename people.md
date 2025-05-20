---
layout: page
title: People
permalink: /people/
---

{% assign people_sorted = site.people | sort: 'joined' %}
{% assign role_array = "pi|postdoc|phd|researchstaff|visiting|others|alumni" | split: "|" %}

{% for role in role_array %}
  {% assign people_in_role = people_sorted | where: 'position', role %}
  {% if people_in_role.size == 0 %}
    {% continue %}
  {% endif %}

  <div class="pos_header">
    {% if role == 'postdoc' %}
      <h3>Postdoctoral Fellows</h3>
    {% elsif role == 'pi' %}
      <h3>Principal Investigator</h3>
    {% elsif role == 'phd' %}
      <h3>Graduate Students</h3>
    {% elsif role == 'researchstaff' %}
      <h3>Research Staff</h3>
    {% elsif role == 'visiting' %}
      <h3>Visiting Scholars</h3>
    {% elsif role == 'others' %}
      <h3>Honorary Members</h3>
    {% elsif role == 'alumni' %}
      <h3>Alumni</h3>
    {% endif %}
  </div>

  {% if role != 'alumni' %}
    <div class="content list people">
      {% for profile in people_in_role %}
        <div class="list-item-people">
          <p class="list-post-title">
            {% if profile.avatar %}
              <a href="{{ profile.url | relative_url }}">
                <img class="profile-thumbnail"
                     src="{{ '/images/people/' | append: profile.avatar | relative_url }}">
              </a>
            {% else %}
              <a href="{{ profile.url | relative_url }}">
                <img class="profile-thumbnail"
                     src="http://evansheline.com/.../Storm-Trooper.jpg">
              </a>
            {% endif %}
            <a class="name" href="{{ profile.url | relative_url }}">
              {{ profile.name }}
            </a>
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

