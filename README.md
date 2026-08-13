# QUORUM — Project Page

Source for the project page of:

> **QUORUM: Multi-View Feature Consensus for Open-Vocabulary SLAM in Dynamic Scenes**
> Zaid Nasser\*, Mikhail Iumanov\*, Tianhao Li\*, Maxim Popov, Jaafar Mahmoud†, Sergey Kolyubin
> Biomechatronics and Energy-Efficient Robotics (BE2R) Lab, ITMO University, Saint Petersburg, Russia
> *\* Equal contribution · † Corresponding author: jaafar.a.mahmoud@itmo.ru*
>
> To be presented at the **3rd Workshop on Neural SLAM (NeuSLAM), ECCV 2026**.

- Code: https://github.com/be2rlab/QUORUM
- arXiv: https://arxiv.org/abs/2604.26067

## About the paper

QUORUM is an online semantic SLAM system in which multi-view high-level features vote for a dense pixel-level
visual-language embedding field. That single field — extracted once per keyframe with RADSeg and PCA-compressed to
D = 256 — is consumed at **four stages** of the SLAM stack: the optical-flow prior, the factor-graph topology, a
cross-view residual inside dense bundle adjustment, and the per-pixel shape of the robust kernel. A *temporal stability
field* aggregates cross-view embedding agreement over a keyframe's neighbourhood, separating genuinely static surfaces
from movable objects and actively moving agents, and maps that to the Barron shape parameter.

The system runs on raw, uncalibrated monocular RGB video at 8–10 FPS — no intrinsics, no depth sensor, no pose prior,
no list of dynamic classes.

## Structure

```
index.html                 Single-page site (all CSS/JS inline, no build step)
static/images/             Figures, favicon, video poster
static/videos/             Hero video
static/css, static/js      Unused template leftovers (bulma, fontawesome)
QUORUM/                    LaTeX sources of the paper (not published by the site)
.nojekyll                  Serve static/ verbatim on GitHub Pages
```

The page has no dependencies and no build step: open `index.html`, or serve the directory
(`python3 -m http.server`) and visit it. Only the Google Fonts stylesheet is fetched externally.

### Figures used on the page

| File on the page                    | Source in `QUORUM/images/` | Shows                                        |
| ----------------------------------- | -------------------------- | -------------------------------------------- |
| `static/images/overview.png`        | `df.png`                   | Fig. 1 — full pipeline                       |
| `static/images/ark.png`             | `ark_1.jpg`                | Fig. 2 — adaptive robust kernels             |
| `static/images/ablation_pca.jpg`    | `ablation_1.jpg`           | Fig. 3 — PCA dimensionality ablation         |
| `static/images/grounding_replica.jpg` | `results.png`            | Fig. 4 — open-vocabulary grounding on Replica |
| `static/images/pca_office.jpg`      | `viz.png`                  | Fig. 5 — in-the-wild office, phone camera    |
| `static/images/pca_replica.jpg`     | `viz2.png`                 | Fig. 6 — RGB-PCA colorization, office 3      |
| `static/images/stream_quad.jpg`     | `11.png`                   | Fig. 7 — live stream, four views             |
| `static/images/teaser_poster.jpg`   | frame 90 of the hero video | Poster frame for the hero video              |

Paper figures were downscaled to ≤1800 px wide and re-encoded as progressive JPEG for page weight.

## Updating the results

Every number in the five tables on the page is transcribed from `QUORUM/tables/*.tex`:

| Page table                       | LaTeX source                        |
| -------------------------------- | ----------------------------------- |
| Table 1 — TUM-RGBD ATE           | `tables/slam-tum.tex`               |
| Table 2 — Replica 3D segmentation | `tables/semantics-replica.tex`      |
| Table 3 — kernel ablation        | `tables/ablation-core.tex`          |
| Table 4 — consumer ablation      | `tables/ablation-consumers.tex`     |
| Table 5 — capability comparison  | `tables/comparison-sota-features.tex` |

If the paper's numbers change, update both the cells and the `rank-1` / `rank-2` / `rank-3` badges, which mirror the
`\best` / `\sbest` / `\tbest` highlighting in the LaTeX.

## Deployment

The repository is served by GitHub Pages from the repository root; `.nojekyll` keeps `static/` intact.

## Acknowledgments

Built on the [Academic Project Page Template](https://github.com/eliahuhorwitz/Academic-project-page-template),
parts of which were adopted from [Nerfies](https://nerfies.github.io/).

## Website License

<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-sa/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Attribution-ShareAlike 4.0 International License</a>.
