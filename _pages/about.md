---
layout: about
title: About
permalink: /
subtitle:

profile:
  align: right
  image: ma_photo.jpg
  image_circular: false # crops the image to make it circular

selected_papers: false # includes a list of papers marked as "selected={true}"
social: false # includes social icons at the bottom of the page

announcements:
  enabled: true # includes a list of news items

latest_posts:
  enabled: false
  scrollable: true
  limit: 3
---

<style>
  /* Desktop : photo petite à droite */
  @media (min-width: 576px) {
    .profile {
      width: 20% !important;
    }
  }

  /* Mobile : photo centrée, taille raisonnable */
  @media (max-width: 575.98px) {
    .profile {
      width: 60% !important;
      max-width: 220px !important;
      float: none !important;
      margin-left: auto !important;
      margin-right: auto !important;
      margin-bottom: 1rem !important;
    }
  }
</style>


Hi, I'm Camille — a final-year PhD candidate at <a href="https://cnes.fr/">CNES</a>, based in Paris, supervised by Bruno Vallet, Dawa Derksen, and Alexandre Constantin.
My research focuses on neural rendering for large-scale 3D reconstruction from satellite imagery. The core challenge: existing methods are slow to train and fail to scale beyond small scenes — both critical barriers to real-world use.

What keeps pulling me back is how unforgiving the satellite setting is for neural methods. A view-dependent appearance model that makes perfect sense on a Blender scene becomes deeply weird when the "camera" is a pushbroom sensor 700 km up and the "lighting" is the sun three weeks later — and once you've made it work on a single crop, the question immediately becomes: how do you scale to a whole country?

---

So far, my PhD has produced two main contributions:

- **[SAT-NGP](https://ieeexplore.ieee.org/document/10641775)** (IGARSS 2024)

- **[Snake-NeRF](https://openaccess.thecvf.com/content/ICCV2025W/3D-VAST/html/Billouard_Tile_and_Slide__A_New_Framework_for_Scaling_NeRF_ICCVW_2025_paper.html)** (ICCV Workshops 2025)

---

Before the PhD, I earned my master's in Artificial Intelligence from **Paul Sabatier University** (Toulouse) in 2023.

I'm currently looking for a **postdoctoral position**, ideally on topics around neural scene representations, large-scale 3D reconstruction, or the geometry–vision–remote sensing interface. Don't hesitate to reach out by email if my profile fits something you're building.
