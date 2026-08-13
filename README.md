# MATTAR Dashboard — Blazor WebAssembly (WASM)

A modern Dashboard UI template built with **Blazor WebAssembly (.NET 8)** and deployed on **GitHub Pages**.

- Demo: https://mattar-shadi.github.io/MATTAR.Dashboard/

> Project goal (upcoming): turn this into a dashboard for tracking Microsoft Store sales (Partner Center integration in a future step).

## ✨ Current Features

- **Blazor WASM** SPA (.NET 8)
- **Dark / light** theme (persisted via `localStorage`)
- Responsive sidebar (hamburger menu + mobile overlay)
- Razor pages: Dashboard, Analytics, Clients, Orders, Finances, Settings
- Charts via **Chart.js** (CDN) + JavaScript (for now)
- Automated deployment to GitHub Pages

## 🧱 Repository Structure

```
.
├── MATTAR Dashboard.csproj
├── Program.cs
├── App.razor
├── _Imports.razor
├── Layout/
├── Pages/
├── wwwroot/
│   ├── index.html
│   ├── css/
│   │   └── style.css
│   └── js/
│       └── main.js
└── .github/workflows/deploy.yml
```

## ✅ Prerequisites

- .NET SDK 8.x

Verify:

```bash
dotnet --version
```

## ▶️ Run Locally (dev)

```bash
git clone https://github.com/mattar-shadi/dashboard-site.git
cd dashboard-site

dotnet restore
dotnet run
```

Then open the URL shown in the console (e.g. `http://localhost:5062`).

## 🏗️ Build / Publish

```bash
# Build
dotnet build

# Publish (Release)
dotnet publish -c Release -o publish
```

The published static files are located in:

- `publish/wwwroot/`

## 🌐 GitHub Pages Deployment

The `.github/workflows/deploy.yml` workflow:

- Builds and publishes in Release mode
- Adjusts `<base href>` to `/dashboard-site/` (since the site is served under a sub-path)
- Generates `404.html` (a copy of `index.html`) to support SPA routing on GitHub Pages
- Adds `.nojekyll`
- Deploys via `actions/deploy-pages`

### Trigger Branch

Note: the workflow triggers on the **`main`** branch.

If your default branch is `master`, you have 2 options:
1. Rename the default branch to `main`
2. Or update the workflow to trigger on `master`

## 🎨 Assets / UI

- CSS: `wwwroot/css/style.css`
- JS: `wwwroot/js/main.js`

## 🗺️ Roadmap (next steps)

- Replace mock data with real data from **Microsoft Partner Center** (sales / revenue / acquisitions)
- Replace part of the JS with Blazor components + minimal interop
- Add a proper data model + services + error handling

## 📄 License

MIT
