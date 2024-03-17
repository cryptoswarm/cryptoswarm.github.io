---
layout: page
title: Terrain generator; cities, ports or villages
description: >
  The aim of the project is to define a procedural terrain generator, which will take as input a geometric mesh (a set of polygons tiling the plane). Based on this mesh, the program will create a terrain (lakes, mountains, villages, roads, forests, etc.), and produce as output an "enriched" mesh that can be visualized.

img: assets/img/tortuga-2-archipelago.png
importance: 1
category: School
github: https://github.com/cryptoswarm/terrain-generator
github_stars: true
show: true
---

Here is the <a href="https://github.com/cryptoswarm/terrain-generator">Github repository</a>

How to use the project?<br>
After cloning the project you can compile it by running the following command
{% raw %}

```html
mvn clean package
```

{% endraw %}
Suppose you aim to create two archipelagos resembling atolls, each featuring three cities, two ports, five villages, and connecting roads. In this case, execute the following command:
{% raw %}

```html
./ptg.sh -i samples/sample-1000-1000-4096.mesh -o demo.mesh --shape atoll
--archipelago 2 --pois cities:3 --pois --ports:2 --pois villages:5 --roads
--water 1 --rivers 2 --seed 150
```

{% endraw %}

The above command will generate:<br>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/atoll.png" title="atoll" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Tranquil Atolls: Twin Archipelagos in Serene Harmony
</div>
