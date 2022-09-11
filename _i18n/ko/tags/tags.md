<ul>
    {% for tag in site.tags %}
    <span style="font-size: {{ tag | last | size | times: 100 | divided_by: site.tags.size | plus: 70 }}%">
        <a href="#{{ tag | first | slugize }}"><span class="text-primary">{{ tag | first }}</span></a>
    </span>
    {% endfor %}
</ul>
<hr />
<div>
    {% for tag in site.tags %}
    <div>
        {% capture tag_name %}{{ tag | first }}{% endcapture %}
        <a name="{{ tag_name | slugize }}"></a>
        <h3 class="section-heading text-primary" id="#{{ tag_name | slugize }}">{{ tag_name }}</h3>
        {% for post in site.tags[tag_name] %}
            <ul>
                <li><a href="{{ post.url }}">{{ post.title }}</a></li>
            </ul>
        {% endfor %}
    </div>
    {% endfor %}
</div>


