
{% for person in people_list %}

{% assign loopindex = forloop.index | modulo: 4 %}

{% if loopindex == 1 %}
<div class="row">
{% endif %}


<div class="medium-3 columns">
<div class="team-member anchor-offset" id="{{ person.github }}">
  {% if person.github %}
  <img data-src="https://avatars.githubusercontent.com/{{ person.github }}" width=128 height=128 class="img-responsive img-circle lazyload" alt="GitHub profile photo of {{person.person_name}}">
  {% else %}
  <img data-src="https://www.gravatar.com/avatar/{{ person.gravatar }}?d=mp" width=128 height=128 class="img-responsive img-circle lazyload" alt="Gravatar profile photo of {{person.person_name}}">
  {% endif %}
  <h3>{{ person.person_name }}</h3>
  <ul class="list-inline social-buttons">
      {% if person.twitter %}<li> <a href="https://twitter.com/{{ person.twitter }}"> <i class="fab fa-twitter" title="Twitter"></i> </a> </li> {% endif %}
      {% if person.github %}<li> <a href="https://github.com/{{ person.github }}"> <i class="fab fa-github" title="GitHub"></i> </a> </li> {% endif %}
      {% if person.orcid %}<li> <a href="https://orcid.org/{{ person.orcid }}"> <i class="fab fa-orcid" title="ORCID"></i> </a> </li> {% endif %}
      {% if person.url and person.url != "" %}<li> <a href="{{ person.url }}"> <i class="fas fa-link" title="Website"></i> </a> </li> {% endif %}
  </ul>
  {% unless person.country == "" %}
  <img width="64" src="/files/flags/{{ person.country | downcase }}.svg" alt={{person.country}} title={{person.country}} />
  {% endunless %}
</div>
</div>


{% if loopindex == 0 %}
</div>
{% endif %}
{% endfor %}



<script>
    var images = document.getElementsByTagName('img')
    // Start loop at 1. Hacky way to avoid the banner image.
    for (let i=1; i < images.length; i++) {
        var regionNames = new Intl.DisplayNames(['en'], {type: 'region'});
        fullName = regionNames.of(images[i].title);
        images[i].title = fullName;
        images[i].alt = fullName;
    }
</script>