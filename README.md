# PlantUML Export Test Repo (Extended: AppSec Processes)

This repo renders PlantUML (`*.puml`) diagrams into images using GitHub Actions, then auto-commits the generated outputs back into the repo.

## Layout

- **Sources:** `diagrams/src/*.puml`
- **Shared includes:** `diagrams/includes/*.puml` (do not render directly)
- **Global config:** `diagrams/config/config.puml` (passed via PlantUML `-config`)
- **Outputs:** 
  - `diagrams/out/png`
  - `diagrams/out/svg`
  - (optional) `diagrams/out/jpg` (converted from PNG)

## AppSec diagrams included

The AppSec process set is stored as `diagrams/src/01-...` through `diagrams/src/13-...` and references the shared include:

- `diagrams/includes/appsec-style.puml`

Each AppSec diagram begins with:

```plantuml
!include ../includes/appsec-style.puml
```

so styling is consistent and the include file is *not* treated as a diagram to render.

## How to add a new diagram

1. Add a `*.puml` file under `diagrams/src/`.
2. If you need shared macros / styling, place them under `diagrams/includes/` and include them from your diagram via a relative path.
3. Push to `main` — the workflow will render and auto-commit images under `diagrams/out/`.
