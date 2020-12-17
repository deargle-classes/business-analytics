---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default
---

# Topics


{%- for topic in site.topics %}
<h3>{{ topic.title }}</h3>
<p>
{% if topic.readings %}
<div>
  Readings
  <ul>
    {% for reading in topic.readings -%}
    <li>{{ reading }}</li>
    {%- endfor %}
  </ul>
</div>
{% endif %}
{% if topic.slides %}
  <div><a href="{{ topic.slides | prepend: '/slides/' | relative_url }}">Slides</a></div>
{%- endif %}
</p>
{%- endfor %}


# Labs

{% for lab in site.labs %}
* [ {{ lab.title }} ]( {{ lab.url | relative_url }})
{%- endfor %}


# Projects

{% for project in site.projects %}
* [ {{ project.title }} ]( {{ project.url | relative_url }})
{%- endfor %}


# Exams

{% for exam in site.exams %}
* [ {{ exam.title }} ]( {{ exam.url | relative_url }})
{%- endfor %}


# External Links

* [Python Labs for the chapters from Provost & Fawcett](https://github.com/ferlocar/spring_2019_data_mining)
