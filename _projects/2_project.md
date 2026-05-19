---
layout: page
title: Snake-NeRF
description: An out-of-core framework that scales NeRF to very large geographic areas on a single GPU, using 3D tile partitioning, a segmented sampler, and a 2×2 progression strategy to avoid boundary artifacts. Linear time complexity, no quality compromise.
img: assets/img/publication_preview/snake_pattern.gif
importance: 1
category: work
giscus_comments: true
---

## Memory and Time Scaling

Figures 1–3 show how peak PyTorch memory, peak NVML memory, peak CPU RSS, and total training time evolve with the number of tiles $$K$$.

Both GPU memory curves stay bounded across the full $$K$$ range, matching the $$4 \cdot S_{\mathrm{NeRF}} + \mathcal{O}(MN)$$ prediction: PyTorch peak in $$0.59$$–$$1.84$$ GB, NVML peak (including custom kernels and the CUDA context $$C_{\text{ctx}}$$) in $$5.5$$–$$11.0$$ GB.

{% include figure.liquid loading="eager" path="assets/img/memory_gpu.png" title="Peak GPU memory vs number of tiles" class="img-fluid rounded z-depth-1" %}

<div class="caption">
    <strong>Figure 1.</strong> Peak GPU memory (PyTorch + NVML) versus number of tiles $$K$$ on the PNEO scene. Solid markers report the maximum over all phases. Our streaming approach (big dot) stays bounded in the $$5.5$$–$$11.0$$ GB band (NVML) and $$0.59$$–$$1.84$$ GB band (PyTorch) regardless of $$K$$.
</div>

CPU memory behaves differently: the two coarsest runs ($$K=1, 4$$) hold the full image cache in host memory and consume $$\sim 98$$ GB of RSS, while all multi-tile runs ($$K \geq 53$$) drop to $$20$$–$$32$$ GB once the cache is itself tiled.

{% include figure.liquid loading="eager" path="assets/img/memory_cpu_nerfxl.png" title="Peak CPU RSS vs number of tiles" class="img-fluid rounded z-depth-1" %}

<div class="caption">
    <strong>Figure 2.</strong> Peak CPU RSS as a function of the number of tiles $$K$$, on the PNEO scene. Solid markers report the maximum over all phases. CPU memory drops by a factor of $${\sim}5$$ between $$K=4$$ and $$K=54$$ because the image cache becomes itself tiled.
</div>

Wall-clock time grows roughly linearly with $$K$$ in the asymptotic regime: the $$17{\times}26$$ run takes $$37.67$$ h, about $$20\times$$ longer than the single-tile run.

{% include figure.liquid loading="eager" path="assets/img/time_scaling.png" title="Total training time vs number of tiles" class="img-fluid rounded z-depth-1" %}

<div class="caption">
    <strong>Figure 3.</strong> Total training time as a function of the number of tiles $$K$$, on the PNEO scene. Markers report the cumulative wall-clock time across all phases. Training time grows roughly linearly with $$K$$ in the asymptotic regime.
</div>

## PSNR vs Tile Area

Figure 4 plots PSNR (delta vs. best run) and training time against tile area $$s$$. Smaller tiles monotonically improve PSNR — the $$17{\times}26$$ run reaches $$21.97$$ dB, $$5.45$$ dB above the single-tile run — but the cost in training time is strongly non-linear:

- $$s = 52.28 \to 13.07$$ km²: $$+0.39$$ dB at near-zero cost ($$1.84 \to 2.54$$ h)
- $$13.07 \to 1.00$$: $$+1.09$$ dB at moderate cost ($$2.54 \to 3.25$$ h)
- $$1.00 \to 0.25$$: $$+2.43$$ dB, but budget grows fivefold ($$3.25 \to 16.75$$ h)
- $$0.25 \to 0.125$$: only $$+1.54$$ dB, doubling wall-clock time again ($$16.75 \to 37.67$$ h)

The knee sits near $$s = 0.25$$ km², beyond which marginal PSNR-per-hour drops sharply.

{% include figure.liquid loading="eager" path="assets/img/ablation_tile_area_km2_delta_psnr.png" title="PSNR delta and training time vs tile area" class="img-fluid rounded z-depth-1" %}

<div class="caption">
    <strong>Figure 4.</strong> PSNR delta vs. best run as a function of target tile area $$s$$ (log scale, blue, left axis) and total training time (orange, right axis). The blue band is the per-tile $$\pm 1\sigma$$ envelope. The training-time curve grows by more than an order of magnitude over the same range.
</div>

## DEM Quality vs Tile Area

DSM accuracy follows the same monotonic trend as PSNR. We use NMAD as the primary indicator: as a robust analog of the standard deviation ($$1.4826 \times \mathrm{median}(|e - \mathrm{median}(e)|)$$), it is insensitive to outliers on building edges and under vegetation, exactly where local geometry is hardest. From the all-class average curve (Figure 5), NMAD drops from $$8.54$$ m at $$s = 52.28$$ km² to $$2.09$$ m at $$s = 0.125$$ km² — a $$4.1\times$$ improvement.

{% include figure.liquid loading="eager" path="assets/img/projects/nerfxl/ablation_tile_area_km2_delta_xdem_nmad_avg.png" title="NMAD vs tile area" class="img-fluid rounded z-depth-1" %}

<div class="caption">
    <strong>Figure 5.</strong> NMAD averaged over the whole scene as a function of $$s$$ (log scale, blue, left axis) and training time (orange, right axis). The green horizontal line marks the best NMAD ($$2.09$$ m at $$s = 0.125$$ km²). The robustness of NMAD to outliers makes this curve the most reliable indicator of bulk DSM quality.
</div>
