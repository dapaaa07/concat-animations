# Concat Animation Templates

Official community repository for downloadable open-source animation presets for [Concat Video Editor](https://github.com/jub0t/Concat).

## Format Specification

Each animation preset is a lightweight JSON file (1-2 KB) with cubic-bezier easing and dynamic value resolution relative to a clip's resting state.

```json
{
  "id": "zoom_in_bounce",
  "name": "Zoom In Bounce",
  "kind": "in",
  "targets": ["all"],
  "defaultDuration": 0.5,
  "minDuration": 0.1,
  "maxDuration": 3.0,
  "tracks": {
    "scale": [
      {
        "t": 0.0,
        "value": { "type": "relative", "value": 0.05 },
        "ease": [0.0, 0.0, 0.2, 1.0]
      },
      {
        "t": 0.72,
        "value": { "type": "relative", "value": 1.18 },
        "ease": [0.4, 0.0, 0.2, 1.0]
      },
      {
        "t": 1.0,
        "value": { "type": "relative", "value": 1.0 },
        "ease": [0.0, 0.0, 0.2, 1.0]
      }
    ],
    "opacity": [
      {
        "t": 0.0,
        "value": { "type": "absolute", "value": 0.0 },
        "ease": [0.0, 0.0, 0.2, 1.0]
      },
      {
        "t": 0.35,
        "value": { "type": "absolute", "value": 1.0 },
        "ease": [0.0, 0.0, 1.0, 1.0]
      }
    ]
  }
}
```

### Supported Properties
- `scale`: Clip scaling factor.
- `offsetX`: Horizontal translation offset in frame widths (-3.0 to 3.0).
- `offsetY`: Vertical translation offset in frame widths (-3.0 to 3.0).
- `rotation`: Rotation in degrees (-360.0 to 360.0).
- `opacity`: Transparency level (0.0 to 1.0).

### Supported Value Types
- `relative`: Multiplied by the clip's current resting value (e.g. `1.15` is 115% scale).
- `offset`: Added to the clip's resting value (e.g. `-1.2` for slide-in from left).
- `absolute`: Fixed constant value (e.g. `0.0` or `1.0` for opacity).

### Easing Curves
- Predefined: `"linear"`, `"in"`, `"out"`, `"inOut"`
- Custom cubic-bezier: `[x1, y1, x2, y2]` where `0.0 <= x <= 1.0`.

## How to Contribute
1. Create a JSON file under `in/`, `out/`, or `combo/`.
2. Register the entry in `index.json`.
3. Open a Pull Request!

## License
MIT License. Free for personal and commercial use.
