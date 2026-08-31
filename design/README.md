# Design Config

This folder controls app colors and course icons for `progressive-webapp`.

## Files

- `colour.yaml`: theme tokens, dashboard tones, course tones, landing accents, ticker colors, and mobile navigation colors.
- `icon.yaml`: course slug to icon file mapping.
- `course-icons/*.svg`: the current course icon files used by the app.

## To add or replace a course icon

1. Put the icon file in `design/course-icons/`
2. Update that course entry inside `design/icon.yaml`
3. Push the repo changes
4. Refresh the web app

Example:

```yaml
react-js:
  label: React JS
  iconPath: design/course-icons/react-js.svg
```
