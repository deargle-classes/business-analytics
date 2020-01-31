---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default
---

# Topics

{%- for topic in site.topics %}
   * [ {{ topic.title }} ]( {{ topic.url }} )
{% endfor -%}


# Labs

{%- for lab in site.labs %}
   * [ {{ lab.title }} ]( {{ lab.url }})
{% endfor -%}


# External Links

[Python Labs for the chapters from Provost & Fawcett](https://github.com/ferlocar/spring_2019_data_mining)
