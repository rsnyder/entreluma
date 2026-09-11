---
layout: page
title: Author Guide
permalink: /admin/
---

Entreluma turns Markdown into interactive visual stories. Start with the [example story]({{ '/monument-valley/' | relative_url }}) and create a file named `_posts/YYYY-MM-DD-your-story.md` using `_posts/.template.md`.

## Write and publish

Edit the title, description, author, categories, and tags in the YAML header. Set `published: true` when the story is ready, and commit to your repository's default branch. GitHub Actions builds and publishes your site.

Store images beside your other story assets in `assets/posts/your-story/` and set `media_subpath: /assets/posts/your-story` in the header. Ordinary Markdown images and viewer sources can then use filenames such as `photo.jpg`.

{% if site.entreluma.editor_url and site.entreluma.editor_url != '' %}
The optional [Entreluma Editor]({{ site.entreluma.editor_url }}) provides a separate authoring interface. You can also write and publish entirely through GitHub's web editor.
{% endif %}

## Add viewers

Each viewer uses a Liquid include. Give it a unique `id` so links in the prose can control it. These examples show the source to put in your Markdown:

{% raw %}
```liquid
{% include embed/image.html id="photo" src="photo.jpg" caption="Describe the image" %}
{% include embed/map.html id="map" center="37.02828,-110.23819" zoom="10" %}
{% include embed/youtube.html id="video" vid="yg0As_HOvJk" %}
{% include embed/iframe.html id="external" src="https://example.org" %}
```
{% endraw %}

Image comparison and network viewers are available through `embed/image-compare.html` and `embed/vis-network.html`; their source includes document supported options. External pages must allow iframe embedding.

## Connect prose to media

```markdown
[Look closer](photo/zoomto/pct:10,20,30,40)
[Visit Monument Valley](map/flyto/37.02828,-110.23819,11)
[Navajo Nation](Q1783171)
```

Action links use the viewer's `id`. Wikidata Q-id links open entity information popups when enabled.

## Choose a layout

The default is a flat reading layout. For a two-column story with pinned media, add this to the YAML header:

```yaml
entreluma:
  mode: 2col
```

Site-wide defaults live under `entreluma` in `_config.yml`. Options include the reading-mode toggle, automatic floating, grouped embeds, entity popups, citation and PDF tools. Set `entreluma: false` on a post to disable the extensions.
