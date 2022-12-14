# Block Theme Requirements: A Review

[Supplemental Video](https://videopress.com/v/1FTYZp6a)

Let's start by reviewing the requirements for a block theme. This is the bare minimum you need to create a working block theme.

> **Note:** If this is the first time you are learning about block themes you might want to first check out the [Develop Your First Low-Code Block Theme course](https://learn.wordpress.org/course/develop-your-first-low-code-block-theme/).

## Requirements

All themes, including block themes, reside in a directory in the `wp-content/themes` directory of your WordPress installation. If you take a look at the `wp-content/themes` directory of your WordPress installation you will see a number of directories, each containing a theme. The directory name of each theme is also known as the theme slug which is used to identify the theme in the WordPress admin.

> **Do:** To begin create a new directory in your `themes` directory, and give the directory a unique name for your new theme.

![Image of themes directory with 'new-block-theme' directory](https://learn.wordpress.org/files/2022/10/new-block-theme.png)

Once you've created your theme folder, your theme must have at minimum a `style.css` file and an `index.php` file. 

### style.css

In a block theme, the `style.css` is primarily used to register the [header comment](https://developer.wordpress.org/themes/basics/main-stylesheet-style-css/#basic-structure) for your theme, which is used to display information about the theme in the Appearance -> Themes dashboard panel. 

![Theme Information](https://learn.wordpress.org/files/2022/10/base-block-theme-01.png)

Here is an example of the Twenty Twenty theme's style.css header comment:

```css
/*
Theme Name: Twenty Twenty
Theme URI: https://wordpress.org/themes/twentytwenty/
Author: the WordPress team
Author URI: https://wordpress.org/
Description: Our default theme for 2020 is designed to take full advantage of the flexibility of the block editor. Organizations and businesses have the ability to create dynamic landing pages with endless layouts using the group and column blocks. The centered content column and fine-tuned typography also makes it perfect for traditional blogs. Complete editor styles give you a good idea of what your content will look like, even before you publish. You can give your site a personal touch by changing the background colors and the accent color in the Customizer. The colors of all elements on your site are automatically calculated based on the colors you pick, ensuring a high, accessible color contrast for your visitors.
Tags: blog, one-column, custom-background, custom-colors, custom-logo, custom-menu, editor-style, featured-images, footer-widgets, full-width-template, rtl-language-support, sticky-post, theme-options, threaded-comments, translation-ready, block-styles, wide-blocks, accessibility-ready
Version: 1.3
Requires at least: 5.0
Tested up to: 5.4
Requires PHP: 7.0
License: GNU General Public License v2 or later
License URI: http://www.gnu.org/licenses/gpl-2.0.html
Text Domain: twentytwenty
This theme, like WordPress, is licensed under the GPL.
Use it to make something cool, have fun, and share what you've learned with others.
*/
```

> **Note** If this is the first time you are seeing these fields, you can learn more about them, and what they are used for in the [Theme Developer Handbook](https://developer.wordpress.org/themes/basics/main-stylesheet-style-css/#explanations).

The minimum required fields for the header comment are `Theme Name`, (the name of the theme) but it's useful to add data for `Theme URI` (the web address where the theme can be downloaded), `Author` (the name of the theme developer), and `Author URI` (a web address where the theme developer can be contacted).

> **Do:** Go ahead and create a new style.css file to your theme, and add the following fields as the header comment, replacing the field values with your own information:

```css
/*
Theme Name: New Block Theme
Theme URI: https://learn.wordpress.org/new-block-theme
Author: Jane Doe
Author URI: https://learn.wordpress.org/
Text Domain: new-block-theme
*/
```

### index.php

The `index.php` file is the theme template file that WordPress will use by default, if it can't find a matching template file for the content being rendered. For the purposes of block themes, this file can be left empty, and just include the PHP opening tag. Some developers like to add a comment to the file to indicate that it is intentionally left blank.

> **Do:** Create your theme's index.php file, and add the following code:

```php
<?php
// Silence is golden.
```

### index.html block template

Block themes require one additional file, and `index.html` template. This file needs to be created inside a new directory in the theme directory called `templates`. This file can be empty, but it is required for the theme to be recognized as a block theme, and enable the Editor option in the Appearance menu.

> **Do:**
> 1. Create your theme's `templates` directory.
> 2. Create your theme's `index.html` file inside this directory, and leave it blank for now.

### theme.json

Finally, a block theme should have a theme.json file. This file handles the global settings and styles for a block theme. While this file is not required for a block theme to be active on a WordPress site, for the purposes of developing your theme, it's extremely useful to create it early on. 

It's not a requirement to add any settings or styles to the theme.json file when starting a new block theme. 

However, it is useful to start by including the JSON schema, as well as setting the theme.json "version", and creating empty fields for the "settings" and "styles". 

> **Note:** The JSON schema is used by code editors to provide things like tooltips, autocomplete, and validation while editing theme.json.

> **Do:** Create your theme's theme.json file in the root of the theme directory, and add the following code:

```
{
  "$schema": "https://schemas.wp.org/trunk/theme.json",
  "version": 2,
  "settings": {
  },
  "styles": {
  }
}
```

Once you've added these required files, you are ready to start developing your block theme.

![Minimum Theme Requirements](https://learn.wordpress.org/files/2022/10/directory-structure.png)

> **Note:** For the rest of this course, you'll be working in your new theme, so go ahead and activate it now from the **Appearance -> Themes** dashboard page.

![Image of new block theme active](https://learn.wordpress.org/files/2022/10/new-block-theme-active.png)

### Further Reading

You can read more about the minimum requirements for setting up a Block Theme in the section on [Block Themes](https://developer.wordpress.org/themes/block-themes/block-theme-setup/) in the Theme Handbook. Also, check out these useful [developer tools and resources](https://developer.wordpress.org/themes/basics/tools-resources/) that will help speed up your block theme development.

In the next two lessons, we'll take a look at the two types of files that make up a block theme, templates and template parts.