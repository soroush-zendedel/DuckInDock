# 🐥 Duck in Dock

🚀 **Open-source guides & tools for web technologies, Docker, and GitHub workflows.**

---

## 🌐 Welcome to Duck in Dock! 🐥⚓🐳
This repository hosts open-source projects, guides, and documentation focused on web technologies, Docker, and GitHub workflows.

✅ **What You'll Find Here:**
- Hands-on tutorials on Docker, web development, and CI/CD.
- Open-source projects and templates for your development needs.
- Best practices for deploying and managing applications in containerized environments.

📌 **Usage:**
Feel free to explore, contribute, and use the resources here! If you use any code, please credit the repository by linking back.

---

## 📦 Open Source & Contribution
All code here is **open-source**, and you're welcome to contribute! If you use any resources, please **credit the repository**.

### 🔗 **Stay Connected**

- 🌍 Website: [GitHub Pages](https://soroush-zendedel.github.io/DuckInDock)
- 📦 GitHub repository: [soroush-zendedel/DuckInDock](https://github.com/soroush-zendedel/DuckInDock)
- 🎥 YouTube: [YouTubeChannel](https://www.youtube.com/@DuckInDock)
- 🐳 Docker Hub: [DockerHubProfile](https://hub.docker.com/u/duckindock)

## Local development with Docker

Docker provides the Ruby and Jekyll environment used to serve and build the site. You do not need to install Ruby or Bundler on your computer.

### Requirements

- Docker Desktop (or Docker Engine) with Docker Compose v2
- An internet connection the first time you build, so Docker can download the Ruby image and Ruby gems

Run all commands below from the repository root.

### Start the development server

Build the Docker image and start Jekyll:

```sh
docker compose up --build
```

Open <http://localhost:4000>. Jekyll watches the mounted project files and rebuilds the local site as you edit them. This local server uses the root path, so you do not need to add `/DuckInDock` to the address.

To run it in the background instead, use `docker compose up --build -d`. View its output with `docker compose logs -f site`, then stop and remove the container with `docker compose down`.

### Build for GitHub Pages

Create the production site with the repository path in its links:

```sh
docker compose run --rm site bundle exec jekyll build --baseurl /DuckInDock -d _site/DuckInDock
```

The generated files are in `_site/DuckInDock`. The `/DuckInDock` base URL is required because this is a project site served at `https://soroush-zendedel.github.io/DuckInDock`; the local development server overrides it to serve from `http://localhost:4000`.

### Docker files

- `Dockerfile` selects Ruby 3.3, installs the gems from `Gemfile`, and defines the Jekyll development server command.
- `compose.yaml` builds and runs the site, mounts the working tree for live edits, and maps port 4000 to the host.
- `.dockerignore` keeps Git metadata, generated output, and local caches out of the Docker build context.

After changing `Gemfile` or the `Dockerfile`, rebuild the image with `docker compose up --build` before starting the site again.

🚢 **Let's build and deploy together!** 🐥⚓

## License
This work is published under [MIT](LICENSE) License.
