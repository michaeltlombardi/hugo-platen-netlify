# hugo-platen-netlify

Hugo module for adding Netlify-isms to your Platen site.
In this initial release, support is added for enabling you to hook your site up to NetlifyCMS for posting and editing blog entries.

## Add Netlify CMS to your site

First, you'll need to update your site configuration to add this module:

```yaml
# config.yaml
module:
  imports:
    - path: github.com/platenio/hugo-platen-netlify
```

Next, you need to add a page to load your CMS on the site;
we suggest `content/admin.md` but it can be named anything you please.
Probably best not to add it to your site menu though!

```markdown
<!-- content/admin.md -->
---
Title: Netlify CMS Administration
type: netlifycms
outputs:
  - HTML
  - netlifycms_config
---
```

Finally, you'll need to try to serve your site and navigate to the admin page!

```sh
hugo serve
```

## Additional Configuration

This theme provides basics to ensure that anything shipped in the Hugo Platen theme is covered;
any Platen modules which extend the base theme are responsible for ensuring their shortcodes and collection types are represented and automatically available on import.

If you're extending things yourself, you may find the upstream [NetlifyCMS Hugo module's documentation useful](https://github.com/theNewDynamic/hugo-module-tnd-netlifycms) - that's the module this one is built on!

Additionally, the [official NetlifyCMS documentation](https://www.netlifycms.org/docs/intro/) is _also_ likely to be useful for you, as it explains and shows examples for building collections and updating the configuration.

## Widgets

This module adds widgets to account for the available shortcodes in the core Platen theme;
additional shortcodes should have their widget definitions shipped as part of their parent module.

[This page of the official NetlifyCMS documentation](https://www.netlifycms.org/docs/custom-widgets/) explains how these widgets work and how to make your own.

To add the newly defined custom widgets to your site, create one (or more) files in the `assets` folder named `netlifycms-name.js` - be sure to replace `name` with whatever makes sense for you.
You can also just name the file `netlifycms.js` if you're only adding the one file.
