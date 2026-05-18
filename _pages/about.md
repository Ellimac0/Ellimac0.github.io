---
layout: about
title: about
permalink: /
subtitle: Final-year PhD candidate at <a href="https://cnes.fr/">CNES</a> (currently in Paris !), working on neural rendering for large-scale 3D reconstruction from satellite imagery — in collaboration with <a href="https://www.umr-lastig.fr/">LASTIG</a> (IGN / Univ Gustave Eiffel / ENSG).

profile:
  align: right
  image: ma_photo.jpg
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
  enabled: false
  scrollable: true
  limit: 3
---

Hi, I'm **Camille** — a final-year PhD candidate at the **French Space Agency (CNES)** in Toulouse, supervised by Bruno Vallet, Dawa Derksen, and Alexandre Constantin. My thesis is conducted in collaboration with the [LASTIG](https://www.umr-lastig.fr/) lab (IGN / Univ Gustave Eiffel / ENSG), where I'm enrolled at Univ Gustave Eiffel.

My research sits at the intersection of **3D computer vision, neural rendering, and Earth observation**. I work on adapting Neural Radiance Fields (NeRF) to satellite imagery — a setting where neural methods have shown elegant ways to handle the messiness of multi-date acquisitions (shadows, seasonal variation, transient objects), but where two practical barriers stand in the way of real use: training takes tens of hours, and existing methods don't scale beyond small scenes.

What keeps pulling me back to this problem is how unforgiving the satellite setting is for neural methods. A view-dependent appearance model that makes perfect sense on a synthetic Blender scene becomes deeply weird when the "camera" is a pushbroom sensor 700 km up and the "lighting" is the sun three weeks later — and once you've made it work on a single crop, the question immediately becomes: how do you scale this to a whole region, a whole country? Training is still expensive — there's no free lunch — but I think we're getting close to the cheapest one on the menu.

---

So far, my PhD has produced two main contributions:

- **[SAT-NGP](https://ieeexplore.ieee.org/document/10641775)** (IGARSS 2024) — bringing satellite NeRF training down from tens of hours to about 15 minutes by combining efficient sampling with multi-resolution hash encoding (à la Instant-NGP), with no loss in reconstruction quality.

- **[Snake-NeRF](https://openaccess.thecvf.com/content/ICCV2025W/3D-VAST/html/Billouard_Tile_and_Slide__A_New_Framework_for_Scaling_NeRF_ICCVW_2025_paper.html)** (ICCV Workshops 2025) — an out-of-core framework that scales NeRF to very large geographic areas on a single GPU, using 3D tile partitioning, a segmented sampler, and a 2×2 progression strategy to avoid boundary artifacts. Linear time complexity, no quality compromise.

---

Before the PhD, I earned my master's in Artificial Intelligence from **Paul Sabatier University** (Toulouse) in 2023.

I'm currently looking for a **postdoctoral position**, ideally on topics around neural scene representations, large-scale 3D reconstruction, or the geometry–vision–remote sensing interface. Don't hesitate to reach out by email if my profile fits something you're building.
