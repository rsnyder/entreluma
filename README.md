# Entreluma

A starter template for publishing interactive stories that weave together words, images, maps, and sources. Built with Jekyll, the [Chirpy theme](https://github.com/cotes2020/jekyll-theme-chirpy), and iframe viewers for images, image comparisons, maps, YouTube, and networks.

Project site: [entreluma.org](https://entreluma.org). The optional [Entreluma Editor](https://editor.entreluma.org) is maintained separately in [rsnyder/entreluma-editor](https://github.com/rsnyder/entreluma-editor). Publishing requires only this repository and GitHub Pages; no editor service or credentials are required.

## Create your site

1. On [rsnyder/entreluma](https://github.com/rsnyder/entreluma), select **Use this template → Create a new repository**. Choose a public repository for free GitHub Pages hosting.
2. Open **Settings → Pages** and set **Source** to **GitHub Actions**.
3. Open **Actions → Build and Deploy**. The first run waits up to 15 minutes for Pages setup. If no run started or the wait expired, select **Run workflow** on `main` (or `master`).
4. Follow the deployment link in the workflow summary. Edit `_config.yml` to set your title, description, avatar, and author details under `social`.
5. Copy `_posts/.template.md` into `_posts/YYYY-MM-DD-your-story.md`, add your story, and commit to the default branch to publish. Delete the example post and its `assets/posts/monument-valley` folder when you no longer need them.

The workflow detects the repository owner, name, site origin, and base path from GitHub Pages. Project sites, account sites, and configured custom domains use the same template. You do not need to edit `url` or `baseurl` for Pages. Branch-based Pages builds are not supported: the theme and custom plugins require the included Actions workflow.

The published author guide is at `/admin/`. The editor is optional; Markdown can be edited directly on GitHub. Set `entreluma.editor_url` in `_config.yml` to change the guide's editor link, or leave it empty to hide it.

## Local development

Use the Ruby version in `.ruby-version` and Bundler:

```sh
bundle install
bundle exec jekyll serve --livereload
```

Open `http://127.0.0.1:4000`. Verify changes with:

```sh
python3 tools/check_consistency.py
bundle exec ruby tools/prove_local_media.rb
bundle exec jekyll build
```

CI also checks internal links. External viewer services require network access in the reader's browser.

## Project hosting

For the canonical repository, enable **Template repository** under **Settings → General**, select GitHub Actions in Pages settings, and configure `entreluma.org` as its custom domain with HTTPS. Configure DNS with the domain provider using [GitHub's custom domain instructions](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site).

The domain belongs in the canonical repository's Pages settings. This template deliberately contains no `CNAME` and no fixed deployment URL, so copies have independent hosting. `editor.entreluma.org` belongs to the separate editor deployment; it is not a route or application in this repository.

See [repository boundaries and migration notes](docs/repository-boundary.md) for the selected source files and the editor integration contract.
