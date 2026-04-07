## xGHub
[CVIU] Official repository of paper **Once Upon a Goal: Towards orientation-based shot metrics in football**
<div align="center">

[![Conference](https://img.shields.io/badge/CVIU-PDF-FBBC04?style=for-the-badge&logo=google-slides&logoColor=black)](https://www.sciencedirect.com/science/article/pii/S1077314226000998)
[![HuggingFace](https://img.shields.io/badge/dataset-%23FFD21E.svg?style=for-the-badge&logo=huggingface&logoColor=white)](https://huggingface.co/datasets/mguti97/xGHub/)

<img src="ezgif-65f45937d42cdf18.gif" width="70%" />
</div>

## Dataset structure

Two top-level directories: `labels/` for per-shot metadata and `videos/` for the raw footage.
```
├── labels/
│   └── 000001/                  # one folder per shot, zero-padded ID
│       └── tabular_data.json    # shot-level metadata (see below)
└── videos/
    └── 000001.mp4               # video clip, filename matches label folder ID
```

### `tabular_data.json` fields

| Field | Type | Description |
|---|---|---|
| `is_goal` | bool | Whether the shot resulted in a goal |
| `mirror_flag` | bool | Whether the clip was horizontally flipped for left-right correction |
| `video_width` | int | Frame width in pixels |
| `video_height` | int | Frame height in pixels |
| `angle_to_goal` | float (°) | Horizontal angle from shooter to goal centre |
| `angle_to_posts` | float (°) | Angular width of the goal as seen by the shooter |
| `distance_from_goal` | float (m) | Euclidean distance to the goal line |
| `body_part` | str | e.g. `"outer foot"`, `"head"`, `"right foot"` |
| `technique` | str | e.g. `"normal"`, `"volley"`, `"half-volley"` |
| `play_pattern` | str | e.g. `"regular"`, `"set piece"`, `"counter"` |
| `shooter_pressure` | float [0–1] | Defensive pressure on the shooter |
| `goal_face_occlusion_def` | float [0–1] | Goal area blocked by outfield defenders |
| `goal_face_occlusion_gk` | float [0–1] | Goal area blocked by the goalkeeper |
| `goal_face_occlusion_joint` | float [0–1] | Combined occlusion (def + gk) |
| `2d_orient_angle` | float (°) | Absolute body orientation in 2-D image space |
| `2d_orient_rel_angle` | float (°) | Body orientation relative to the goal in 2-D |
| `2d_f_3d_orient_angle` | float (°) | 3-D orientation projected to 2-D (absolute) |
| `2d_f_3d_orient_rel_angle` | float (°) | Same, relative to the goal |
| `3d_orient_angle` | float (°) | Full 3-D body orientation (absolute) |
| `3d_orient_rel_angle` | float (°) | 3-D orientation relative to the goal |
| `3d_orient_elev_angle` | float (°) | Elevation angle of body lean in 3-D |
| `match_code` | str | `"YYYY-MM-DD-Home vs. Away"` source match identifier |
