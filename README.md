# Story Cast

A three-page media microsite exploring Sudanese culture, music, and landscapes through audio, embedded YouTube performances, and photography. Built with semantic HTML and Sass, without a frontend framework.

## Pages

- **Home (`index.html`):** introduces Sudan, features a culture recording with an expandable on-page transcript and a plain-text transcript link, and presents music and landscape photography.
- **Music (`story/sound_of_sudan.html`):** presents Sudanese performances with expandable descriptions and links to YouTube.
- **About / Accessibility (`about.html`):** explains the site's mission, navigation, and accessibility features.

## Project structure

```text
storycast/
├── index.html
├── about.html
├── story/
│   └── sound_of_sudan.html
├── sass/
│   ├── main.scss
│   ├── _colors.scss
│   ├── _typography.scss
│   └── _spacing.scss
├── css/
│   ├── main.css
│   └── main.css.map
├── assets/
│   ├── audio/
│   ├── images/
│   └── transcripts/
├── package.json
└── README.md
```

## Run locally

Install Node.js and npm, then run these commands from the project folder:

```sh
npm ci
npx sass --watch sass/main.scss css/main.css
```

Keep the Sass watcher running while editing. In another terminal, if Python 3 is installed, start a local server:

```sh
python3 -m http.server 3000
```

Open [Story Cast locally](http://localhost:3000). Internet access is required for YouTube videos. Stop either process with `Ctrl+C`.

To compile Sass once instead of watching:

```sh
npx sass sass/main.scss css/main.css
```

Edit files in `sass/`; `css/main.css` and its source map are generated output.

## Styling approach

- Color, typography, and spacing tokens are defined in Sass partials and loaded with `@use`.
- BEM classes identify components and their elements, such as `site-header__brand`.
- The `base` and `components` cascade layers organize foundation and component styles.
- Flexbox arranges navigation and card content; CSS Grid arranges media cards.
- Container queries switch cards to two columns when their containing section is at least `40rem` wide. Narrower containers use a stacked layout.
- Images scale with their available space, and embedded videos use a 16:9 aspect ratio.

## Accessibility checklist

Implemented in source; browser and assistive-technology testing is still required:

- [x] English document language and descriptive page titles.
- [x] Semantic landmarks and section headings.
- [x] Alternative text for content images.
- [x] Native audio controls on Home.
- [x] A complete, expandable on-page transcript for the culture recording, with timestamps and speaker labels.
- [x] A plain-text version of the audio transcript available through a separate link.
- [x] Focus styling for links and scrollable description regions.
- [x] Native `details` and `summary` controls for the audio transcript and expandable performance descriptions.
- [x] Keyboard-focusable scrollable description regions.
- [x] Responsive layout rules using Grid, Flexbox, and container queries.
- [x] Every iframe has exactly one descriptive title.
- [ ] Verify caption availability and accuracy for every embedded performance.
- [x] Verify the audio transcript against the recording.
- [x] Measure horizontal overflow on all three pages at 320, 375, 768, and 1440px.
- [x] Verify all internal links, media playback, and external destinations.

## Media and credits

- The culture recording was created by Nawaf Ahmed and is stored in `assets/audio/Exploring Sudan.mp3`; its transcript is in `assets/transcripts/sudanese-culture.txt`.
- The transcript is also included in Home's “Read the recording transcript” expandable section. It preserves speaker labels, timestamps, and uncertainty notes; it is a readable text alternative rather than synchronized captions. When correcting the transcript, update both the on-page and plain-text versions.
- The hero image (`assets/images/hero_mountain.png`) is an original photograph by Nawaf Ahmed.
- The musician photograph is credited on Home to almoseqar via Wikimedia Commons, with a CC BY-SA 4.0 attribution. Verify the source attribution and license before submission.
- The landscape collage is credited on Home to Nawaf Ahmed, with an Instagram link.
- Performances are embedded from YouTube and linked to their source videos.

Document the source, creator, and applicable permission or license for all media in the final documentation.
