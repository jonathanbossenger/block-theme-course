# Registering a Block Pattern in a Theme


![WordPress block editor with a Cover block selected and a drop-down with the Copy Blocks option selected.](/images/module-06/lesson-02/copy-pattern.png)

## Register a Pattern via the /patterns Folder

The recommended method of registering a block pattern is by creating a new PHP file within a `/patterns` folder in your theme.  It's best to give it a filename that matches your pattern.  In this case, that would be `hero.php`.  

Create this file in your theme so that your theme structure looks like the following:

- `themeslug`
	- `/patterns`
		- `/hero.php`
	- ...

Themes registered via the `/patterns` folder require a file header with information about the pattern.  At the very least, all patterns require a `Title` and `Slug` field.  A `Categories` field is strongly recommended too so that it's easier for users to find patterns related to what they're looking for.

Enter the following code into your `hero.php` file.  Let's give it the minimum fields needed to become a pattern.

```php
<?php
/**
 * Title: Hero
 * Slug: themeslug/hero
 * Categories: featured
 */
?>
<!-- Pattern code goes here. -->
```

> **Note**
> The `Slug` field should be namespaced based on your theme folder name.  So, if your theme's slug is `super-duper`, your `Slug` value becomes `super-duper/hero`.

There are several file header fields that you may choose from (remember that `Title` and `Slug` are required):

- **Title:** A human-readable title that can be translated.
- **Slug:** A namespaced slug that is unique to your pattern in the form of `namespace/pattern-name`.
- **Categories:** A comma-separated list of categories in which the pattern belongs.
- **Description:** The long description of the registered pattern. Only shown to screen readers.
- **Viewport Width:** The width of the `<iframe>` viewport when previewing the pattern (in pixels).
- **Inserter:** Whether to show the pattern in the inserter.  Defaults to `true`.
- **Keywords:** A comma-separated list of keywords related to the pattern for search.
- **Block Types:** A comma-separated list of block types to associate the pattern with.
- **Post Types:** A comma-separated list of post types in which to limit the pattern. Defaults to all post types.

_Remember the block code that you copied earlier in this lesson?_  Replace the `<!-- Pattern code goes here. -->` line from your `hero.php` file with it.  Your entire file should look similar to the following code snippet:

```php
<?php
/**
 * Title: Hero
 * Slug: themeslug/hero
 * Categories: featured
 */
?>
<!-- wp:cover {"overlayColor":"contrast","align":"full"} -->
<div class="wp-block-cover alignfull"><span aria-hidden="true" class="wp-block-cover__background has-contrast-background-color has-background-dim-100 has-background-dim"></span><div class="wp-block-cover__inner-container"><!-- wp:group {"style":{"spacing":{"blockGap":"2.5rem"}},"layout":{"type":"constrained","wideSize":"%","contentSize":"75%"}} -->
<div class="wp-block-group"><!-- wp:heading {"textAlign":"center"} -->
<h2 class="has-text-align-center">Welcome to My Site</h2>
<!-- /wp:heading -->

<!-- wp:paragraph {"align":"center"} -->
<p class="has-text-align-center">This is my little home away from home. Here, you will get to know me.  I'll share my likes, hobbies, and more.  Every now and then, I'll even have something interesting to say in a blog post.</p>
<!-- /wp:paragraph -->

<!-- wp:buttons {"layout":{"type":"flex","justifyContent":"center"}} -->
<div class="wp-block-buttons"><!-- wp:button {"className":"is-style-outline"} -->
<div class="wp-block-button is-style-outline"><a class="wp-block-button__link wp-element-button">See My Popular Posts →</a></div>
<!-- /wp:button --></div>
<!-- /wp:buttons --></div>
<!-- /wp:group --></div></div>
<!-- /wp:cover -->
```

Save your progress in your code editor.  Now, open a new post or page in the WordPress admin and click the **+** (block inserter) button in the editor.  Then, select the **Patterns** tab.  You should see your Hero pattern listed under the **Featured** category, as shown in the following screenshot:

![WordPress post editor with an empty content canvas and a left sidebar panel showing a list of patterns.](/images/module-06/lesson-02/pattern-in-inserter.jpg)

## Register a Pattern via functions.php

## Register a Pattern Category

## Deregister Patterns (include removing core support)
