---
layout: about
title: about
permalink: /
subtitle: Final-year PhD candidate at <a href="https://cnes.fr/">CNES</a> (Toulouse), working on neural rendering for large-scale 3D reconstruction from satellite imagery — in collaboration with <a href="https://www.umr-lastig.fr/">LASTIG</a> (IGN / Univ Gustave Eiffel).

profile:
  align: right
  image: prof_pic.jpg
  image_circular: true # crops the image to make it circular
  more_info: >
    <p>Office [numéro]</p>
    <p>[Adresse du labo]</p>
    <p>[Ville], France</p>

selected_papers: true # includes a list of papers marked as "selected={true}"
social: true # includes social icons at the bottom of the page

announcements:
  enabled: true # includes a list of news items

latest_posts:
  enabled: false # includes a list of the newest posts
  scrollable: true # adds a vertical scroll bar if there are more than 3 new posts items
  limit: 3 # leave blank to include all the blog posts
---

Hi, I'm **Camille** — a final-year PhD candidate at the **French Space Agency
(CNES)** in Toulouse, working under the supervision of [Bruno Vallet](https://www.umr-lastig.fr/bruno-vallet/),
Dawa Derksen, and Alexandre Constantin. My thesis is conducted in collaboration
with the [LASTIG](https://www.umr-lastig.fr/) lab at IGN / Univ Gustave Eiffel,
where I'm enrolled at ENSG.

My research sits at the intersection of **3D computer vision, neural rendering,
and Earth observation**. I work on adapting Neural Radiance Fields (NeRF) to
satellite imagery — a setting where classical stereo-vision pipelines struggle
with shadows, seasonal variation, and transient objects across acquisitions
taken months or years apart.

What I find genuinely exciting about this problem is that satellite NeRFs sit
at a sweet spot where ideas from graphics, geometry, and remote sensing all
have to talk to each other. A view-dependent appearance model that makes
perfect sense on a synthetic Blender scene becomes deeply weird when the
"camera" is a pushbroom sensor 700 km up and the "lighting" is the sun three
weeks later.

My PhD has focused on two main contributions:

- **SAT-NGP** — bringing satellite NeRF training down from tens of hours to
  about 15 minutes by combining efficient sampling with multi-resolution hash
  encoding (à la Instant-NGP), with no loss in reconstruction quality.
- **Snake-NeRF** — an out-of-core framework that scales NeRF to very large
  geographic areas on a single GPU, using 3D tile partitioning, a segmented
  sampler, and a 2×2 progression strategy to avoid boundary artifacts. Linear
  time complexity, no quality compromise.

Before the PhD, I earned my master's in Artificial Intelligence from
Paul Sabatier University (Toulouse) in 2023.

I'm currently looking for a **postdoctoral position** starting in November 2026,
ideally on topics around neural scene representations, large-scale 3D
reconstruction, or the geometry–vision–remote sensing interface. Don't
hesitate to reach out by email if my profile fits something you're building.
