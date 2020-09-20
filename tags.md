---
layout: post
title:
permalink: /tags/
content-type: eg
---

<!-- ### By Tags -->

<style>
.tagsList{
    margin-left: 0;
}
.category-content a {
    text-decoration: none;
    color: #4183c4;
}

.category-content a:hover {
    text-decoration: underline;
    color: #4183c4;
}
</style>

<main class="tagsList">
    {% for tag in site.tags %}
        <h5 id="{{ tag | first }}" style="margin-bottom: 1rem;">{{ tag | first | capitalize }}</h5>
        {% for post in tag.last %} 
            <li id="category-content" style="padding-bottom: 0.6em; list-style: none;"><a href="{{post.url}}">{{ post.title }}</a></li>
        {% endfor %}
    {% endfor %}
    <br/>
    <br/>
</main>
