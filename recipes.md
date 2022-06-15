---
layout: category
title: Recipes
description: Recipes
category: recipes
permalink: /recipes/
include: true
---

## Sites

{% for recipe in site.recipes %}
### [{{recipe.title}}]({{site.baseurl}}{{recipe.url}})

{% endfor %}
