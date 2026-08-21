# FastWAM-IDM @ LIBERO-Plus

Results for FastWAM-IDM evaluated on LIBERO-Plus.

Obtained using upstream FastWAM at [`7faa711`](https://github.com/yuantianyuan01/FastWAM/commit/7faa71108368fbb3b6885649f112af607427a2d4).

The Optional IDM checkpoint supports both inference modes without retraining.

| Variant | Checkpoint | Inference mode | LIBERO-Plus SR |
| --- | --- | --- | ---: |
| Base FastWAM | `libero_uncond_2cam224.pt` | FastWAM, no test-time imagination | **50.69%** |
| Optional IDM | `libero_optional_idm_2cam224.pt` | `first_frame`, no test-time imagination | **62.14%** |
| Optional IDM | `libero_optional_idm_2cam224.pt` | `idm`, test-time imagination | **70.58%** |

| Axis | n | Base FastWAM | Optional IDM (`first_frame`) | Optional IDM (`idm`) | Co-training gain | Imagination gain |
| --- | ---: | ---: | ---: | ---: | ---: | ---: |
| Robot Initial States | 1,550 | 44.39% | 59.48% | 69.10% | +15.10 pp | +9.61 pp |
| Camera Viewpoints | 1,599 | 15.57% | 30.14% | 42.96% | +14.57 pp | +12.82 pp |
| Sensor Noise | 1,601 | 39.04% | 50.91% | 58.53% | +11.87 pp | +7.62 pp |
| Background Textures | 1,076 | 50.74% | 61.06% | 60.22% | +10.32 pp | -0.84 pp |
| Language Instructions | 1,537 | 70.66% | 80.87% | 94.80% | +10.21 pp | +13.92 pp |
| Objects Layout | 1,525 | 62.10% | 71.34% | 82.36% | +9.25 pp | +11.02 pp |
| Light Conditions | 1,142 | 82.57% | 89.84% | 89.58% | +7.27 pp | -0.26 pp |

`n` is the number of LIBERO-Plus task instances
in each axis. `co-train` is the gain from base FastWAM to Optional IDM in
`first_frame` mode; `imagination` is the additional gain from `first_frame` to
`idm`.

