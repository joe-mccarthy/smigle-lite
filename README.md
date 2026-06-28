# Smigle Lite

![GitHub Actions Workflow Status](https://img.shields.io/github/actions/workflow/status/joe-mccarthy/smigle-lite/deploy-example.yml?branch=main&cacheSeconds=1&style=for-the-badge)
![Sonar Quality Gate](https://img.shields.io/sonar/quality_gate/joe-mccarthy_smigle-lite?server=https%3A%2F%2Fsonarcloud.io&cacheSeconds=1&style=for-the-badge)
![GitHub Release](https://img.shields.io/github/v/release/joe-mccarthy/smigle-lite?sort=semver&cacheSeconds=1&style=for-the-badge)
![GitHub commits since latest release](https://img.shields.io/github/commits-since/joe-mccarthy/smigle-lite/latest?cacheSeconds=1&style=for-the-badge)
![GitHub License](https://img.shields.io/github/license/joe-mccarthy/smigle-lite?cacheSeconds=1&style=for-the-badge)

## Overview

Smigle Lite is a minimalist Hugo theme focused on simplicity, performance, and privacy. It was created as a streamlined alternative to the original [Smigle](https://gitlab.com/ian-s-mcb/smigle-hugo-theme) theme, removing unnecessary elements while maintaining the core principles of being lightweight with no JavaScript or tracking.

### Core Principles

* **No JavaScript by Default** - Pure HTML and CSS unless optional static search is enabled
* **No Tracking** - No Google analytics, cookies, or any user tracking
* **No Runtime External Dependencies** - Bundled JetBrains Mono, no comment sections, tracking, or CDN resources
* **Minimal Design** - Focus on content without distractions

## Features

### Key Differences from Original Smigle

Smigle Lite streamlines the original theme by:

* Removing the user profile image requirement
* Eliminating the site tagline
* Removing reading time estimates
* Removing word count displays
* Simplifying post metadata presentation
* Bundling JetBrains Mono locally
* Improving prose, table, figure, blockquote, footnote, and code styling
* Adding optional table of contents support
* Adding optional static search with a built-in provider and Pagefind support
* Adding JSON-LD, Open Graph, Twitter card, canonical, and author metadata
* Adding accessible skip links and active navigation state
* Adding small content shortcodes for figures, asides, details, and external links
* Redesigning taxonomy pages as simple lists with counts
* Updating the footer with proper attributions
* Various spacing improvements and CSS optimizations
* Post Navigations
* Recent Posts displayed on each post configurable in the config file

### Theme Structure

```
smigle-lite/
├── archetypes/         # Template files for new content
├── example-site/       # Demo site with example content
├── layouts/            # Hugo template files
└── static/             # Static files (images, etc.)
```

## Installation

### As a Git Submodule (Recommended)

From the root of your Hugo site:

```bash
git submodule add https://github.com/joe-mccarthy/smigle-lite themes/smigle-lite
```

Then, update your site's configuration file to use the theme:

```yaml
# config.yaml
theme: smigle-lite
```

Or for TOML:

```toml
# config.toml
theme = "smigle-lite"
```

### Direct Download

1. Download the [latest release](https://github.com/joe-mccarthy/smigle-lite/releases/latest)
2. Extract into your site's `themes` directory
3. Update your site's configuration file as shown above

## Quick Start Guide

### Creating a New Site with Smigle Lite

```bash
# Create a new Hugo site
hugo new site mysite -f yaml
cd mysite

# Add theme
git init
git submodule add https://github.com/joe-mccarthy/smigle-lite themes/smigle-lite

# Edit config.yaml to set theme: smigle-lite
echo 'theme: smigle-lite' >> config.yaml

# Create a new post
hugo new content/posts/my-first-post.md

# Start development server
hugo server
```

### Running the Example Site

To see a demo of the theme:

```bash
git clone https://github.com/joe-mccarthy/smigle-lite
cd smigle-lite/example-site
hugo server --themesDir ../.. --theme smigle-lite
```

Then visit [http://localhost:1313/smigle-lite/](http://localhost:1313/smigle-lite/) in your browser.

## Configuration Reference

Smigle Lite offers extensive configuration options to customize your site. Below is a complete reference based on the provided example configuration file.

### Basic Configuration

```yaml
baseURL: https://example.org/  # Your site's base URL
languageCode: en-gb  # Language code for your site
title: Site Title  # Your site's title
theme: smigle-lite  # Theme name

pagination.pagerSize: 10  # Number of posts per page

markup:
  highlight:
    noClasses: false  # Use the theme's Chroma CSS classes
```

### Menu Configuration

Configure the main navigation menu that appears at the top of your site:

```yaml
menu:
  main:
  - identifier: home  # Unique identifier for the menu item
    name: Home  # Display name
    url: /  # URL path
    weight: 1  # Order in menu (lower values appear first)
  - identifier: about
    name: About
    url: /about/
    weight: 2
  - identifier: posts
    name: Posts
    url: /posts/
    weight: 3
  - identifier: categories
    name: Categories
    url: /categories/
    weight: 5
  - identifier: tags
    name: Tags
    url: /tags/
    weight: 6
  - identifier: series
    name: Series
    url: /series/
    weight: 7
  - identifier: search
    name: Search
    url: /search/
    weight: 8
```

### Theme Parameters

Smigle Lite provides several customization parameters:

```yaml
params:
  # Site author (appears in the footer)
  author: Blog Author

  # Site description (appears in metadata)
  description: "This is the example site description. From Configuration"

  # Default Open Graph / Twitter image
  images:
  - android-chrome-512x512.png

  # Sections shown on the home page and latest-post lists
  mainSections:
  - posts

  # Visual customization
  style:
    maxWidth: 820px
    accentColor: "#386f64"
    darkAccentColor: "#9cd4c2"

  # Display toggles
  display:
    footerAttribution: true
    taxonomyMeta: true

  # Table of contents on single posts with headings
  toc:
    enabled: true
    title: Contents

  # Optional static search. Use "simple" or "pagefind".
  search:
    enabled: true
    provider: simple

  # Latest posts section on single post pages
  latest:
    enabled: true  # Enable/disable latest posts section
    count: 3  # Number of posts to display
  
  # Content license information (appears in footer)
  license:
    name: CC BY-SA 4.0
    url: https://creativecommons.org/licenses/by-sa/4.0/#main-content-marker
  
  # Date format configurations
  abbrDateFmt: "01/02"  # Abbreviated date format for lists
  dateFmt: "06/01/02"  # Full date format for post meta
  
  # Social links (appears in footer)
  social:
  - name: GitHub
    url: https://github.com/joe-mccarthy/smigle-lite
  - name: "RSS"
    url: index.xml
  
  # Post navigation options
  post_nav:
    enabled: true  # Enable/disable previous/next navigation
    show_title: false  # Show post titles in navigation
```

#### Date Format Reference

The date format uses Go's time formatting syntax:

- `01`: Month (numeric)
- `02`: Day (numeric)
- `06`: Year (2-digit)
- `2006`: Year (4-digit)
- `Jan`: Month (abbreviated)
- `January`: Month (full name)

Examples:
- `"01/02"` becomes "07/15" for July 15
- `"06/01/02"` becomes "23/07/15" for July 15, 2023
- `"January 2, 2006"` becomes "July 15, 2023"

### Taxonomies Configuration

Configure how content is categorized:

```yaml
taxonomies:
  category: categories  # URL will be /categories/category-name/
  tag: tags  # URL will be /tags/tag-name/
  series: series  # URL will be /series/series-name/
```

When `series` is enabled, the theme renders a dedicated `/series/` terms page and individual series listing pages. Add a `Series` menu item if you want it in the main navigation.

The theme ships layouts for categories, tags, and series. Additional custom taxonomies should provide matching layouts in your site.

## Complete Example Configuration

For reference, here's a complete example configuration that demonstrates all available options:

```yaml
baseURL: https://example.org/
languageCode: en-gb
title: Site Title
theme: smigle-lite

pagination.pagerSize: 10

markup:
  highlight:
    noClasses: false

menu:
  main:
  - identifier: home
    name: Home
    url: /
    weight: 1
  - identifier: about
    name: About
    url: /about/
    weight: 2
  - identifier: posts
    name: Posts
    url: /posts/
    weight: 3
  - identifier: categories
    name: Categories
    url: /categories/
    weight: 5
  - identifier: tags
    name: Tags
    url: /tags/
    weight: 6
  - identifier: series
    name: Series
    url: /series/
    weight: 7
  - identifier: search
    name: Search
    url: /search/
    weight: 8

params:
  author: Blog Author
  description: "This is the example site description. From Configuration"
  images:
  - android-chrome-512x512.png
  mainSections:
  - posts
  style:
    maxWidth: 820px
    accentColor: "#386f64"
    darkAccentColor: "#9cd4c2"
  display:
    footerAttribution: true
    taxonomyMeta: true
  toc:
    enabled: true
    title: Contents
  search:
    enabled: true
    provider: simple
  latest:
    enabled: true
    count: 3
  license:
    name: CC BY-SA 4.0
    url: https://creativecommons.org/licenses/by-sa/4.0/#main-content-marker
  abbrDateFmt: "01/02"
  dateFmt: "06/01/02"
  social:
  - name: GitHub
    url: https://github.com/joe-mccarthy/smigle-lite
  - name: "RSS"
    url: index.xml
  post_nav:
    enabled: true
    show_title: false

taxonomies:
  category: categories
  tag: tags
  series: series
```

This configuration should be saved as `config.yaml` in your Hugo site's root directory.

## Content Configuration

### Front Matter Examples

Each content file in Hugo can have front matter that determines how it's processed and displayed:

```yaml
---
title: "My First Post"
date: 2023-07-15T10:00:00
draft: false
categories: ["Technology"]
tags: ["hugo", "tutorial"]
series: ["Getting Started"]
summary: "A quick introduction to Smigle Lite"
images:
- posts/my-first-post/cover.jpg
toc: true
---
```

For pages that should appear in the menu:

```yaml
---
title: "About Me"
menu:
  main:
    weight: 2
---
```

## Customization

### Custom CSS

To add your own CSS customizations, create a file such as `static/css/custom.css` in your site root and list it under `params.customStylesheets`.

Example configuration:

```yaml
params:
  customStylesheets:
  - css/custom.css
```

Example custom CSS:

```css
/* static/css/custom.css */
body {
  font-family: 'Your Preferred Font', sans-serif;
}

.site-header {
  background-color: #f0f0f0;
}
```

### Content Organization

Smigle Lite works best with the following content structure:

```
content/
├── posts/           # Blog posts
├── pages/           # Static pages
└── about/           # About page
    └── index.md
```

### Front Matter Options

```yaml
---
title: "My Post Title"
date: 2023-07-15T10:00:00-05:00
draft: false
categories: ["Technology"]
tags: ["hugo", "tutorial"]
series: ["Getting Started"]
summary: "Optional summary that will be displayed in lists"
---
```

## Advanced Usage

### Table of Contents

Set `params.toc.enabled: true` to show a generated table of contents on single pages that contain headings. Override it per page:

```yaml
---
toc: false
---
```

### Custom Shortcodes

Smigle Lite includes a few small shortcodes:

```markdown
{{< figure src="image.jpg" alt="Description" caption="A local image caption." >}}

{{< aside title="Note" >}}
Short supporting text.
{{< /aside >}}

{{< details summary="More context" >}}
Hidden-by-default details.
{{< /details >}}

{{< external-link href="https://gohugo.io/" text="Hugo documentation" >}}
```

### Image Handling

Markdown images are responsive by default. For captions, use the bundled figure shortcode:

```markdown
{{< figure src="/images/my-image.jpg" alt="Image description" caption="Image caption" >}}
```

For social previews, set `images` in page front matter or `params.images` in your site config.

### Syntax Highlighting

The theme provides Chroma class styles. Enable class-based highlighting:

```yaml
markup:
  highlight:
    noClasses: false
```

### Static Search

Search is optional and off by default. The built-in `simple` provider creates a small client-side index from regular Hugo pages:

1. Create a search page with `layout: search`
2. Set `params.search.enabled: true`
3. Set `params.search.provider: simple`

For larger sites, set `params.search.provider: pagefind`, build the Hugo site, then run Pagefind against the generated site, for example `pagefind --site public`. The Pagefind provider loads `/pagefind/pagefind-ui.css` and `/pagefind/pagefind-ui.js` from your own site.

### Taxonomies

Customize how taxonomies are displayed by editing your site's configuration:

```yaml
taxonomies:
  category: categories
  tag: tags
  series: series
```

## Updating the Theme

To update the theme when used as a git submodule:

```bash
git submodule update --remote --merge
```

Or for all submodules:

```bash
git submodule foreach git pull origin main
```

## Troubleshooting

### Common Issues

1. **Theme not loading**: Ensure your `config.yaml` has `theme: smigle-lite` (or `theme = "smigle-lite"` in TOML)

2. **Styling problems**: Check for CSS conflicts with custom CSS

3. **Missing content**: Verify your content is not marked as `draft: true` unless using the `--buildDrafts` flag

## Contributing

Contributions to Smigle Lite are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch: `git checkout -b my-new-feature`
3. Commit your changes: `git commit -am 'Add some feature'`
4. Push to the branch: `git push origin my-new-feature`
5. Submit a pull request

Before submitting your PR, please:
- Ensure your code follows the project's style
- Test your changes thoroughly
- Update documentation as needed

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgements

* [Ian S. McBride](https://gitlab.com/ian-s-mcb) - Author and maintainer of the Hugo [Smigle](https://gitlab.com/ian-s-mcb/smigle-hugo-theme) theme
* [colorchestra](https://github.com/colorchestra) - Maintainer of [smol](https://github.com/colorchestra/smol) theme
* [Hugo](https://gohugo.io/) - The static site generator that makes this all possible

## Version History

See the [Releases](https://github.com/joe-mccarthy/smigle-lite/releases) page for the changelog and version history.
