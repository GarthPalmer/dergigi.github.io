---
layout: page
title: Media Appearances
subtitle: Interviews, Movies, and more.
redirect_from: /interviews

---

[✨ All (no filter)][all] | [⭐ Favorites][favs] | [🇺🇸 English][en] | **🇩🇪 German**

[all]: {{ '/media' | absolute_url }}
[favs]: {{ '/media/favs' | absolute_url }}
[de]: {{ '/media/de' | absolute_url }}
[en]: {{ '/media/en' | absolute_url }}


{% assign sorted_sodes = site.episodes | where: 'lang', 'DE' | sort: 'date' | reverse %}

<ul class="sodes">
{% for sode in sorted_sodes %}
  {% assign link = sode.youtube %}
  {% if sode.podlink %}{% assign link = sode.podlink %}{% endif %}
  {% if sode.link %}{% assign link = sode.link %}{% endif %}
  <li>
    <a href="{{ link }}" target="_blank" title="Released on {{ sode.date }} by {{ sode.host }}">
      {% if sode.star %} ⭐ {% endif %}
      {% case sode.lang %}
        {% when 'AT' %}🇦🇹
        {% when 'DE' %}🇩🇪
        {% when 'CH' %}🇨🇭
        {% else %}🇺🇸
      {% endcase %}
      {% if sode.youtube %}📺{% else %}🎧{% endif %}
      {{ sode.podname }}
      {% if sode.sode %}#{{ sode.sode }} {% endif %}
    </a>
    <small>
      {% if sode.podlink %}<a href="{{ sode.podlink }}" target="_blank"><i class="fab fa-podcast"></i></a>{% endif %}
      {% if sode.youtube %}<a href="{{ sode.youtube }}" target="_blank"><i class="fab fa-youtube"></i></a>{% endif %}
      {% if sode.archive %}<a href="{{ sode.archive }}" target="_blank"><i class="fab fa-archive"></i></a>{% endif %}
      <br/>
      {% if sode.topics %}on {{ sode.topics }},{% endif %}
      {% if sode.guests %}with {{ sode.guests }}{% endif %}
      {% if sode.host %}hosted by {{ sode.host }}{% endif %}
    </small>

  </li>
{% endfor %}
</ul>
