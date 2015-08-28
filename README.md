Jekyll-Invert
=============

A liquid include file for Jekyll that allows one-to-one and one-to-many relations to be inverted. For instance, it could be used to list posts by author or by tag.

Usage
-----

Copy the [`jekyll-invert.html`](https://raw.githubusercontent.com/mushishi78/jekyll-invert/master/jekyll-invert.html) file into your Jekyll project's `_includes` directory.

Include the file in your template, passing in a `collection` and a `field` variable. Then Jekyll-Invert will set `inverted-keys` and `inverted-values` global variables with the results.

For example:

``` liquid
---
layout: page
title: Tags
---

{% include jekyll-invert.html collection=site.posts field='tags' %}

<ul>
  {% for tag in inverted_keys %}
    {% assign posts = inverted_values[forloop.index0] %}

    <li>
      <h2>{{ tag }}</h2>
      <ul>
        {% for post in posts %}
        <li>
          <a href='{{ site.baseurl }}{{ post.url }}'>{{ post.title }}</a>
        </li>
        {% endfor %}
      </ul>
    </li>
  {% endfor %}
</ul>
```

For an extended example, checkout out this [jekyll-invert example branch](https://github.com/mushishi78/fresh-jekyll/tree/jekyll-invert-example) of the Fresh Jeykll repository.

Contributing
------------

1. [Fork it](https://github.com/mushishi78/jekyll-invert/fork)
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create a new Pull Request