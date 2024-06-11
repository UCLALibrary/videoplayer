# Simple Video Player

This is a simple single-page app for viewing wowza video streams. It is configured via URL parameters:

- _`src`_ A URL-escaped link to the video stream. Depending on the characters used, you can sometimes get away with not escaping.
- _`title`_ Optional title displayed on page.

Examples:

- https://static.library.ucla.edu/staticvideo/index.html?title=Pan%20African%20Orchestra&src=https%3A%2F%2Fwowza.library.ucla.edu%2Fiiif_av_public%2Fdefinst%2Fmp4%3AMEAP%2Fpairtree_root%2F21%2F19%2F8%3D%2Fz1%2F5j%2F28%2F75%2F21198%3Dz15j2875%2Fark%252B%3D21198%3Dz15j2875.mp4
- https://static.library.ucla.edu/staticvideo/index.html?title=Home%20movie%20with%20Laura%20Huxley,%20Virginia%20Pfeiffer%20and%20family%20in%20Hollywood%20Hills%20home.%20Reel%202&src=https%3A%2F%2Fwowza.library.ucla.edu%2Fiiif_av_public%2Fdefinst%2Fmp4%3Ahuxle%2Fpairtree_root%2F21%2F19%2F8%3D%2Fzz%2F00%2F2k%2F4h%2Fq1%2F21198%3Dzz002k4hq1%2Fark%252B%3D21198%3Dzz002k4hq1.mp4
- https://static.library.ucla.edu/staticvideo/index.html?title=Accidental%20Host&src=https://wowza.library.ucla.edu/staticvideos/AccidentalHost/mp4:accidental_host_20230212_1080p.mp4 (Only playable on UCLA Network)

## Recommended IDE Setup

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur).

## Customize configuration

See [Vite Configuration Reference](https://vitejs.dev/config/).

## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Compile and Minify for Production

```sh
npm run build
```

### Run Unit Tests with [Vitest](https://vitest.dev/)

```sh
npm run test:unit
```

### Lint with [ESLint](https://eslint.org/)

```sh
npm run lint
```
