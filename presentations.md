---
title: Reference
permalink: /presentations/
---

### Upcoming lab meetings

Every two weeks on Mondays at 11:00 UTC, we get together (in person) for lab presentations (with food! sometimes).
On a rotating basis, each member of the lab speaks and teaches about something they know or shares their work. 
Anything, really. Relevant and interesting topics, good statistic skills to know, new findings and literature reviews... anything!

### Winter 2025
{% raw %}
| Date       | Name | Topic |
|------------|------|-------|
| Aug 4      | Xindong Zhang| Neural mechanisms of tone processing and MEG techique |
| Aug 4 (additional) | Junjie Wu  | Similarity analyses and permutation analyses   |
| Aug 18      | TBD | TBD |


{% endraw %}



{% assign reference_types = "scientists|students" | split: "|" %}

{% for type in reference_types %}

{% if type == 'scientists' %}
### **For scientists**
 {% elsif type == 'students' %}
### **For students, lab members**
{% endif %}

<div class="content list">
  {% for post in site.posts %}
    {% if post.categories contains type %}
    <div class="list-item">
      <p class="list-post-title">
        <a href="{{ site.baseurl }}{{ post.url }}">- {{ post.title }}</a>
      </p>
    </div>
    {% endif %}
  {% endfor %}
</div>

<hr>
{% endfor %}

