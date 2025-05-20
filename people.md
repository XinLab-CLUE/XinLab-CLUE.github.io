---
title: People
permalink: /people/
---

{% assign people_sorted = site.people | sort: "joined" %}
{% assign roles = "pi|postdoc|phd|researchstaff|visiting|others|alumni" | split: "|" %}

{% for role in roles %}
  {% assign grp = people_sorted | where: "position", role %}
  {% if grp.size > 0 %}

    <h3>
    {% case role %}
      {% when "pi" %}Principal Investigator
      {% when "postdoc" %}Postdoctoral Fellows
      {% when "phd" %}PhD Candidates
    
    {% endcase %}
    </h3>

    <ul class="people-list">
      {% for member in grp %}
        <li>
          <a href="{{ member.url | relative_url }}">
            <img src="{{ "/images/people/" | append: member.avatar | relative_url }}"
                 alt="{{ member.name }}" width="80" />
            {{ member.name }}
          </a>
        </li>
      {% endfor %}
    </ul>

  {% endif %}
{% endfor %}



