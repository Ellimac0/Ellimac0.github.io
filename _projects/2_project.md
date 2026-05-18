---
layout: page
title: Mon Projet
description: a project featuring a research poster
img: assets/img/img_project_iccv.png
importance: 1
category: work
giscus_comments: true
---

Every project has a beautiful feature showcase page.
Here you can present your research poster alongside descriptions and images.

<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/1.jpg" title="project overview" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/3.jpg" title="project detail" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    A brief overview of the project. Left, the initial setup. Right, the results.
</div>

Here is a short description of the project before revealing the poster.
We worked hard, iterated, and finally produced something worth sharing.

## Poster

<div class="row justify-content-sm-center">
    <div class="col-sm-10 mt-3 mt-md-0">
        <iframe src="{ '/assets/pdf/poster_iccv-2.pdf' | relative_url }"
                width="100%"
                height="800px"
                style="border: none; border-radius: 8px;"
                class="z-depth-1">
        </iframe>
    </div>
</div>
<div class="caption">
    Full research poster. You can also download it <a href="{'/assets/pdf/poster_iccv-2.pdf' | relative_url }">here</a>.
</div>
