# Personal Portfolio - svaza.github.io

A clean, modern, single-page portfolio website built for GitHub Pages. Features a configuration-driven approach for easy content updates without touching the UI code.

## 🚀 Features

- **Single HTML file** — No build process required
- **Dark/Light theme toggle** — Persisted in localStorage
- **Fully responsive** — Mobile-first design
- **Configuration-driven** — Edit content in one place (`CONFIG` object)
- **Zero dependencies** — Uses React/ReactDOM via CDN
- **GitHub Pages ready** — Deploy instantly

## 🛠️ Tech Stack

- **React 18** (UMD via CDN)
- **Babel Standalone** (JSX transformation in browser)
- Pure CSS with CSS custom properties (theming)
- No build tools or bundlers required

## 📝 How to Customize

All content lives in the `CONFIG` object within [index.html](index.html). Simply edit the configuration sections:

### Profile Information
```javascript
profile: {
  name: "Your Name",
  headline: "Your Title",
  careerStartYear: 2012, // Used to calculate years of experience
  photoPath: "assets/profile.jpg",
  tagline: "Your professional tagline",
  personalLine: "Personal interests",
  highlights: ["Skill 1", "Skill 2", ...],
  socialProfiles: [
    { key: "github", label: "GitHub", href: "https://github.com/..." },
    // Add more social links
  ],
}
```

### About Section
```javascript
about: {
  title: "About",
  paragraphs: [
    "First paragraph...",
    "Second paragraph...",
  ],
}
```

### Hobby Projects
```javascript
hobbyProjects: {
  title: "Hobby projects",
  intro: "Introduction text",
  items: [
    {
      name: "Project Name",
      subtitle: "Short description",
      description: "Longer description",
      techStack: ["Tech 1", "Tech 2"],
      links: [
        { label: "Live", href: "https://..." },
        { label: "Repo", href: "https://..." },
      ],
    },
  ],
}
```

### Skills & Strengths
```javascript
skillGroups: [
  { title: "Category", chips: ["Skill 1", "Skill 2"] },
  // Add more groups
]

coreStrengths: [
  {
    tone: "ok", // or "warn"
    icon: "✅",
    title: "Strength Title",
    text: "Description",
  },
]
```

## 📸 Profile Photo

Add your profile photo at `assets/profile.jpg` (or update `photoPath` in the config to point to your image location).

## 🏃 Local Development

1. Clone the repository:
   ```bash
   git clone https://github.com/svaza/svaza.github.io.git
   cd svaza.github.io
   ```

2. Open `index.html` directly in a browser, or use a local server:
   ```bash
   # Python 3
   python -m http.server 8000

   # Node.js (using npx)
   npx http-server -p 8000
   ```

3. Visit `http://localhost:8000`

## 🌐 Deployment

This site is designed for **GitHub Pages**:

1. Push your changes to the `main` (or `master`) branch
2. Go to repository Settings → Pages
3. Set source to deploy from `main` branch, `/` (root)
4. GitHub will automatically deploy your site to `https://<username>.github.io`

## 📄 License

This is a personal portfolio site. Feel free to fork and customize for your own use.

## 👤 Contact

- **GitHub**: [@svaza](https://github.com/svaza)
- **LinkedIn**: [svaza](https://www.linkedin.com/in/svaza)

---

Built with ❤️ for simplicity and speed
