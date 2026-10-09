# Stackers — Developer Portfolio

A team JavaScript project: an interactive portfolio website for the fictional developer Jefferson. The page combines a project showcase, skills, reviews and a contact form with configurable visual themes.

[Team demo](https://mykhaito.github.io/stackers-js-project/)

## Features

- Responsive navigation and mobile menu.
- About and FAQ sections with accordions.
- Swiper sliders for skills, projects and reviews.
- Animated project-cover section.
- Dark and light themes with six accent colours.
- Theme preferences saved in `localStorage`.
- Contact form with email validation, a request to an external API, a confirmation modal and error notifications.
- Back-to-top control.

Reviews are rendered from data stored in the frontend. Contact submissions use the GoIT training API; the repository does not contain its own backend.

## Stack

HTML5, CSS3, JavaScript modules and Vite 5.

The interface uses Swiper, Accordion.js, Axios, iziToast and modern-normalize. HTML partials are composed with `vite-plugin-html-inject`.

## Run locally

With Node.js and npm installed:

```sh
git clone https://github.com/Slavik756/stackers-js-project.git
cd stackers-js-project
npm ci
npm run dev
```

Open the URL printed by Vite, normally [http://localhost:5173](http://localhost:5173).

| Command | Purpose |
| --- | --- |
| `npm run dev` | Start development with live updates |
| `npm run build` | Build the site into `dist/` |
| `npm run preview` | Serve the production build locally |

The production build uses `/stackers-js-project/` as its base path. Open the full preview URL printed in the terminal.

## Structure

```text
src/
├── index.html       # Page composition
├── main.js          # Section-module imports
├── partials/        # HTML for each section and modal
├── css/             # Base, section, animation and theme styles
└── js/              # Section-specific behaviour
vite.config.js
.github/workflows/deploy.yml
```

Useful entry points:

- [Theme settings](src/js/settings-for-theme-color.js): CSS variables, accent colours and saved preferences.
- [Contact form](src/js/workTogether.js): validation, API request and result handling.
- [Reviews](src/js/reviews.js): local review data and slider setup.
- [Projects](src/js/projects.js): project-slider interactions.

## Contact API

The form sends an email and comment to:

```text
POST https://portfolio-js.b.goit.study/api/requests
```

A successful response opens the confirmation modal; a failed request displays an error notification. This behaviour depends on the availability of the external training service. Use demonstration data when trying the form.

## Publishing and checks

The GitHub Actions workflow builds pushes to `main` and publishes `dist/` to `gh-pages`. Configure GitHub Pages to serve that branch. Update the build script's base path if deploying under a different repository name or URL path.

There is no automated test command in the current package scripts. After interface changes, check navigation, keyboard-controlled sliders, theme persistence after a reload, form validation and request-error handling.

## Team context

This is a collaborative learning project based on the GoIT Vite starter. The portfolio persona and project content belong to the demonstration website; they are not a claim about every contributor's personal work.
