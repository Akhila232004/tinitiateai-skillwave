# Slideshows

This folder stores markdown slideshow content for the CBT section of the app.

## Goal

Allow the UI to build slideshow decks from markdown content fetched from GitHub.

## Structure

- `av-metadata.yaml`
- `decks/<deck-name>/slideshow-content.md`

## Slide Rule

Use `---` between slides inside a markdown deck.

## How To Add A New Deck

1. Add the deck entry in `av-metadata.yaml`
2. Create the deck folder
3. Add `slideshow-content.md`
4. Keep the slide order inside the markdown file
