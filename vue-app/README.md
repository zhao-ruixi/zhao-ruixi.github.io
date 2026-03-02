# Vue Dashboard with PrimeVue

A beautiful Vue 3 dashboard built with PrimeVue components, designed for GitHub Pages deployment.

## Features

- 🎨 Modern UI with PrimeVue components (Card, DataTable, Button, Sidebar, etc.)
- 📱 Responsive design with PrimeFlex grid system
- 📊 Sample dashboard with stats cards, data tables, and activity feeds
- 🔧 Easy deployment to GitHub Pages
- ⚡ Built with Vite for fast development and production builds

## Project Structure

```
vue-app/
├── src/
│   ├── App.vue          # Main dashboard component
│   ├── main.js          # Vue app entry point with PrimeVue config
│   ├── style.css        # Global styles
│   └── components/      # Additional Vue components
├── index.html           # HTML template with CDN links
├── vite.config.js       # Vite configuration
└── package.json         # Dependencies and scripts
```

## Getting Started

### Installation

```bash
npm install
```

### Development

Start the development server:

```bash
npm run dev
```

Open [http://localhost:5173](http://localhost:5173) to view the dashboard.

### Build for Production

```bash
npm run build
```

The built files will be in the `dist` directory.

### Preview Production Build

```bash
npm run preview
```

## Deployment to GitHub Pages

### Option 1: Deploy to root of GitHub Pages

If you want the dashboard at `https://zhao-ruixi.github.io`:

1. Build the project:
   ```bash
   npm run build
   ```
2. Copy the contents of `dist` folder to the root of your repository
3. Commit and push changes

### Option 2: Deploy to subdirectory

If you want the dashboard at `https://zhao-ruixi.github.io/vue-app/`:

1. Build with subdirectory base:
   ```bash
   npm run build:gh-pages
   ```
2. Copy the contents of `dist` folder to a `vue-app` directory in your repository
3. Commit and push changes

### Option 3: Automatic deployment with gh-pages

Install gh-pages globally (`npm install -g gh-pages`) then run:

```bash
npm run deploy
```

This will build and deploy to the `gh-pages` branch.

## Customization

- Edit `src/App.vue` to modify the dashboard layout
- Update `src/style.css` for custom styles
- Change theme by modifying CDN link in `index.html`
- Add more PrimeVue components as needed

## Dependencies

- [Vue 3](https://vuejs.org/) - Progressive JavaScript framework
- [PrimeVue](https://primevue.org/) - UI component library
- [PrimeFlex](https://primeflex.org/) - CSS utility library
- [PrimeIcons](https://primefaces.org/primeicons/) - Icon library
- [Vite](https://vite.dev/) - Build tool and dev server

## License

MIT