---
layout: category
title: Recipes
description: Recipes
category: Recipes
permalink: /recipes/
include: true
---

## Recipes

{% for recipe in site.recipes %}
### [{{recipe.title}}]({{site.baseurl}}{{recipe.url}})

{% endfor %}
