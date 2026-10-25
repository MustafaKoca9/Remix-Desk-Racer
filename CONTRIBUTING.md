# Contributing to Desk Racer

Thank you for your interest in contributing to **Desk Racer**! Whether you are fixing bugs, optimizing physics or graphics performance, enhancing procedural audio, or suggesting new desk circuit features, we welcome your contributions.

---

## 🧭 Code of Conduct

Please review and adhere to our [Code of Conduct](CODE_OF_CONDUCT.md) in all project interactions.

---

## 🛠️ Development Workflow

### 1. Fork & Clone
```bash
git clone https://github.com/YOUR_USERNAME/desk-racer.git
cd desk-racer
```

### 2. Install Dependencies
```bash
npm install
```

### 3. Create a Feature Branch
```bash
git checkout -b feature/your-feature-name
# or for bug fixes:
git checkout -b fix/issue-description
```

### 4. Run the Local Development Server
```bash
npm run dev
```
Open `http://localhost:3000` in your browser.

### 5. Check Types & Build Integrity
Before pushing your changes, ensure TypeScript compilation and the production build succeed without errors:
```bash
npm run lint
npm run build
```

---

## 📝 Coding Standards & Guidelines

- **Three.js & Graphics**:
  - Always clean up geometry, textures, materials, and render targets when disposing objects to prevent GPU memory leaks.
  - Maintain 60 FPS performance budgets on standard devices. Avoid expensive per-frame heap allocations inside `requestAnimationFrame`.
- **Physics**:
  - Keep vehicle dynamics grounded in Rapier3D. Ensure time-step consistency when adjusting forces or raycasts.
- **Audio**:
  - Always respect the user's mute state. Synthesized nodes must disconnect or gracefully release gain when stopped.
- **Git Commits**:
  - Write clear, concise commit messages using Conventional Commits format:
    - `feat: add night mode desk lamp lighting`
    - `fix: resolve kart clipping on spiral drop`
    - `perf: optimize bokeh blur sample count`
    - `docs: update setup steps in README`

---

## 📬 Submitting a Pull Request

1. Push your branch to your forked repository:
   ```bash
   git push origin feature/your-feature-name
   ```
2. Open a Pull Request against the `main` branch.
3. Fill out the [Pull Request Template](.github/PULL_REQUEST_TEMPLATE.md) with details about your change and any screenshots or clips showing the feature in action.
4. Ensure the CI checks pass.

Thank you for helping make Desk Racer even better!
