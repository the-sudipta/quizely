# Contributing

Thank you for considering a contribution to Quizely.

## Project Goals

Quizely should stay:

- Free to use.
- Easy to host as a static site.
- Private by default.
- Friendly for students on desktop and mobile.
- Simple enough to run without a build system.

## Local Development

Clone the repository and open `index.html` directly, or run:

```bash
python -m http.server 4177
```

Then visit `http://127.0.0.1:4177/`.

## Contribution Ideas

- Accessibility improvements.
- More CSV validation feedback.
- Optional timers.
- Question and option randomization.
- Local-only progress history.
- More import formats while preserving the no-backend model.

## Pull Request Checklist

- Keep the app usable as a static site.
- Avoid adding external network dependencies.
- Test with a CSV that includes quoted commas.
- Check desktop and mobile layouts.
- Update docs when behavior changes.
