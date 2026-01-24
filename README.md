# The Midnight theme

[![.github/workflows/ci.yaml](https://github.com/Frederisk/Midnight-Enhanced/actions/workflows/ci.yaml/badge.svg)](https://github.com/Frederisk/Midnight-Enhanced/actions/workflows/ci.yaml)

*Midnight is a Jekyll theme for GitHub Pages. You can [preview the theme to see what it looks like](http://pages-themes.github.io/midnight), or even [use it today](#usage).*

![Thumbnail of Midnight](thumbnail.png)

## Usage

To use the Midnight theme:

1. Add the following to your site's `_config.yml`:

    ```yml
    remote_theme: Frederisk/Midnight-Enhanced@v0.2.0
    plugins:
    - jekyll-remote-theme # add this line to the plugins list if you already have one
    ```

2. Optionally, if you'd like to preview your site on your computer, add the following to your site's `Gemfile`:

    ```ruby
    gem "github-pages", group: :jekyll_plugins
    ```

## Customizing

### Configuration variables

Midnight will respect the following variables, if set in your site's `_config.yml`:

```yml
title: [The title of your site]
tagline: [A very short description of your site's purpose, used as subtitle]
description: [A short description of your site's purpose (e.g. for search engines)]
```

Additionally, you may choose to set the following optional variables:

```yml
show_downloads: ["true" or "false" (unquoted) to indicate whether to provide a download URL]
google_analytics: [Your Google Analytics tracking ID]
```

### Language

By default, the language of your website, which is the `lang` attribute on the `<html>` tag, is set to `en-US`. You can change this by setting the `lang` variable in your site's `_config.yml`:

```yml
lang: zh-TW
```

Furthermore, you can also set a specific language for each page by adding the `lang` variable to the page's front matter:

```markdown
---
lang: zh-TW
---

# 這是一個中文頁面
```

### Stylesheet

If you'd like to add your own custom styles:

1. Create a file called `/assets/css/style.scss` in your site
2. Add the following content to the top of the file, exactly as shown:

    ```scss
    ---
    ---

    @import "{{ site.theme }}";
    ```

3. Add any custom CSS (or Sass, including imports) you'd like immediately after the `@import` line

*Note: If you'd like to change the theme's Sass variables, you must set new values before the `@import` line in your stylesheet.*

### Configurable JavaScript and CSS

If you'd like to able to freely import certain JavaScript or CSS into specific pages or sites, you can create the necessary file in the `assets/utils/js` or `assets/utils/css` directories. Then use the following configuration at the top of your page or in your site's `_config.yml`:

```yml
custom_css: [ css_file1, css_file2 ] # without the `assets/utils/(css/js)/` prefix and `.css/.js` suffix
custom_js: js_file # For a single file, you can omit the array syntax
```

In particular, the `MathJax` has been predefined in `assets/utils/js/` to provide mathematical formula rendering support. To enable it, simply add the following to your page's front matter or your site's `_config.yml`:

```yml
custom_js: MathJax
```

### Layouts

If you'd like to change the theme's HTML layout:

1. For some changes such as a custom `favicon`, you can add custom files in your local `_includes` folder. The files [provided with the theme](https://github.com/pages-themes/midnight/tree/master/_includes) provide a starting point and are included by the [original layout template](https://github.com/pages-themes/midnight/blob/master/_layouts/default.html).
1. For more extensive changes, [copy the original template](https://github.com/pages-themes/midnight/blob/master/_layouts/default.html) from the theme's repository
    (*Pro-tip: click "raw" to make copying easier*)
1. Create a file called `/_layouts/default.html` in your site
1. Paste the default layout content copied in the first step
1. Customize the layout as you'd like

### Customizing Google Analytics code

Google has released several iterations to their Google Analytics code over the years since this theme was first created. If you would like to take advantage of the latest code, paste it into `_includes/head-custom-google-analytics.html` in your Jekyll site.

### Overriding GitHub-generated URLs

Templates often rely on URLs supplied by GitHub such as links to your repository or links to download your project. If you'd like to override one or more default URLs:

1. Look at [the template source](https://github.com/pages-themes/midnight/blob/master/_layouts/default.html) to determine the name of the variable. It will be in the form of `{{ site.github.zip_url }}`.
2. Specify the URL that you'd like the template to use in your site's `_config.yml`. For example, if the variable was `site.github.url`, you'd add the following:

    ```yml
    github:
      zip_url: http://example.com/download.zip
      another_url: another value
    ```

3. When your site is built, Jekyll will use the URL you specified, rather than the default one provided by GitHub.

*Note: You must remove the `site.` prefix, and each variable name (after the `github.`) should be indent with two space below `github:`.*

For more information, see [the Jekyll variables documentation](https://jekyllrb.com/docs/variables/).

## Roadmap

See the [open issues](https://github.com/pages-themes/midnight/issues) for a list of proposed features (and known issues).

## Project philosophy

The Midnight theme is intended to make it quick and easy for GitHub Pages users to create their first (or 100th) website. The theme should meet the vast majority of users' needs out of the box, erring on the side of simplicity rather than flexibility, and provide users the opportunity to opt-in to additional complexity if they have specific needs or wish to further customize their experience (such as adding custom CSS or modifying the default layout). It should also look great, but that goes without saying.

## Contributing

Interested in contributing to Midnight? We'd love your help. Midnight is an open source project, built one contribution at a time by users like you. See [the CONTRIBUTING file](docs/CONTRIBUTING.md) for instructions on how to contribute.

### Previewing the theme locally

If you'd like to preview the theme locally (for example, in the process of proposing a change):

1. Clone down the theme's repository (`git clone https://github.com/pages-themes/midnight`)
2. `cd` into the theme's directory
3. Run `script/bootstrap` to install the necessary dependencies
4. Run `bundle exec jekyll serve` to start the preview server
5. Visit [`localhost:4000`](http://localhost:4000) in your browser to preview the theme

### Running tests

The theme contains a minimal test suite, to ensure a site with the theme would build successfully. To run the tests, simply run `script/cibuild`. You'll need to run `script/bootstrap` once before the test script will work.
