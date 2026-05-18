---
layout: about
title: about
permalink: /
subtitle: Final-year PhD candidate at <a href="https://cnes.fr/">CNES</a> (Toulouse), working on neural rendering for large-scale 3D reconstruction from satellite imagery — in collaboration with <a href="https://www.umr-lastig.fr/">LASTIG</a> (IGN / Univ Gustave Eiffel / ENSG).

profile:
  align: right
  image: prof_pic.jpg
  image_circular: true # crops the image to make it circular
  more_info: >
    <p><strong>CNES</strong> — French Space Agency</p>
    <p>18 avenue Édouard Belin</p>
    <p>31400 Toulouse, France</p>

selected_papers: true # includes a list of papers marked as "selected={true}"
social: true # includes social icons at the bottom of the page

announcements:
  enabled: true # includes a list of news items

latest_posts:
  enabled: false # set to true once you start blogging
  scrollable: true
  limit: 3
---

Hi, I'm **Camille** — a final-year PhD candidate at the **French Space Agency
(CNES)** in Toulouse, supervised by [Bruno Vallet](https://www.umr-lastig.fr/),
Dawa Derksen, and Alexandre Constantin. My thesis is conducted in collaboration
with the [LASTIG](https://www.umr-lastig.fr/) lab at IGN /
where I'm enrolled at Univ Gustave Eiffel.

My research sits at the intersection of **3D computer vision, neural rendering,
and Earth observation**. I work on adapting Neural Radiance Fields (NeRF) to
satellite imagery — a setting where neural methods have shown elegant ways to
handle the messiness of multi-date acquisitions (shadows, seasonal variation,
transient objects), but where two practical barriers stand in the way of real
use: training takes tens of hours, and existing methods don't scale beyond
small scenes.

What keeps pulling me back to this problem is how unforgiving the satellite
setting is for neural methods. A view-dependent appearance model that makes
perfect sense on a synthetic Blender scene becomes deeply weird when the
"camera" is a pushbroom sensor 700 km up and the "lighting" is the sun three
weeks later — and once you've made it work on a single crop, the question
immediately becomes: how do you scale this to a whole region, a whole
country? **[Snake-NeRF](https://github.com/Ellimac0/Snake-NeRF)** training 
is still expensive in time : there's no free lunch ...  
but it might be the cheapest one on the menu right now.

My PhD has focused on two main contributions:

- **[SAT-NGP](https://github.com/Ellimac0/SAT-NGP)** (IGARSS 2024) — bringing
  satellite NeRF training down from tens of hours to about 15 minutes by
  combining efficient sampling with multi-resolution hash encoding (à la
  Instant-NGP), with no loss in reconstruction quality.
- **[Snake-NeRF](https://github.com/Ellimac0/Snake-NeRF)** (ICCV Workshops 2025)
  — an out-of-core framework that scales NeRF to very large geographic areas
  on a single GPU, using 3D tile partitioning, a segmented sampler, and a 2×2
  progression strategy to avoid boundary artifacts. Linear time complexity, no
  quality compromise.

Before the PhD, I earned my master's in Artificial Intelligence from
**Paul Sabatier University** (Toulouse) in 2023.

I'm currently looking for a **postdoctoral position**, ideally on topics
around neural scene representations, large-scale 3D reconstruction, or the
geometry–vision–remote sensing interface. Don't hesitate to reach out by email
if my profile fits something you're building.
