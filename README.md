Jekyll Group-By-Array
=====================

A liquid include file for Jekyll that allows an object to be grouped by an array. For instance, it could be used to list posts by tag.

Usage
-----

Copy the [`group-by-array.html`](https://raw.githubusercontent.com/mushishi78/jekyll-group-by-array/master/group-by-array.html) file into your Jekyll project's `_includes` directory.

Include the file in your template, passing in a `collection` and a `field` variable. Then Jekyll Group-By-Array will set `group-names` and `group-items` global variables with the results.

For example:

``` liquid
---
layout: page
title: Tags
permalink: /tags/
---

{% include group-by-array.html collection=site.posts field='tags' %}

<ul>
  {% for tag in group_names %}
    {% assign posts = group_items[forloop.index0] %}

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

For an extended example, checkout out this [group-by-array example branch](https://github.com/mushishi78/fresh-jekyll/tree/jekyll-group-by-array) of the Fresh Jekyll repository.

Contributing
------------

1. [Fork it](https://github.com/mushishi78/jekyll-group-by-array/fork)
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create a new Pull Request