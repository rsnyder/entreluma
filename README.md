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

## Update template copies

Template copies include a manifest-driven sync tool for reusable framework files. Check a copy for upstream drift, review the affected paths, and then apply the update:

```sh
python3 tools/sync_code.py --check
python3 tools/sync_code.py --apply
```

Site configuration, stories, media, branding, and local documentation are not overwritten. See [Syncing Entreluma template copies](docs/upstream-sync.md) for the complete ownership boundary, pinned revisions, and local-checkout usage.

## Project hosting

`rsnyder/entreluma` is the generic template. Its optional demo uses the default GitHub Pages project URL. The promotional site and its custom domain are maintained in [rsnyder/entreluma-site](https://github.com/rsnyder/entreluma-site); the editor is maintained in `rsnyder/entreluma-editor`.

This template contains no `CNAME`, fixed deployment URL, owner identity, verification code, or analytics ID. Copies get their own GitHub Pages URL and repository identity from the workflow. Set your title, description, and optional social identity in `_config.yml`, and replace the homepage and About introduction before requesting search indexing.

For a custom domain, configure it in your own repository's Pages settings using [GitHub's custom domain instructions](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site). Never copy another site's domain or verification codes.
