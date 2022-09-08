# Block Theme Requirements: A Review

Let's start by reviewing the requirements for a block theme. We'll do this by looking at the block theme we started with in the [Create a Block Theme (Low-Code) course](https://learn.wordpress.org/create-a-block-theme/).

## Requirements



All themes, including block themes, need a style.css file. WordPress uses the header comment section of the style.css to display information about the theme in the Appearance -> Themes dashboard panel. Additionally the WordPress Theme Repository uses data in the header comment to display information about the theme in the Theme Repository.

Here is an example of a the Twenty Twenty-Three theme's style.css header comment:

```css
/*
Theme Name: Twenty Twenty-Three
Theme URI: https://github.com/WordPress/twentytwentythree
Author: wordpressdotorg
Author URI: https://wordpress.org
Description:
Requires at least: 5.9
Tested up to: 6.1
Requires PHP: 5.6
Version: 0.0.1
License: GNU General Public License v2 or later
License URI: https://www.gnu.org/licenses/old-licenses/gpl-2.0.html
Template:
Text Domain: twentytwentythree
Tags: one-column, custom-colors, custom-menu, custom-logo, editor-style, featured-images, full-site-editing, rtl-language-support, theme-options, threaded-comments, translation-ready, wide-blocks
*/
```

Block themes require one additional file, and index.html template. This file needs to be created inside a directory in the theme directory called `templates`. This file can be empty, but it is required for the theme to be recognized as a block theme, and enable the Editor option in the Appearance menu.

Finally, a block theme needs a theme.json file. This file handles the global settings and styles for a block theme. While it's not required to add any settings or styles to the theme.json file when starting a new block theme, it's useful to start by setting the theme.json "version", and creating empty fields for the "settings" and "styles".

```json
{
  "version": 2,
  "settings": {
  },
  "styles": {
  }
}
```

![Minimum theme requirements for a block theme](/images/module-01/base-block-theme-01.png)