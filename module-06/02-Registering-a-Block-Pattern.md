# Registering a Block Pattern in a Theme

Now that you've built a custom pattern in the previous lesson, it is time to bundle it with your theme.  Doing this will allow the users of the theme to insert it into any block-capable area, such as posts and pages.

To register a pattern, you first need the block code.  You can get this by clicking on the **⋮** (Options) button in the block toolbar.  In the dropdown that appears, select the **Copy block** option.

![WordPress block editor with a Cover block selected and a drop-down with the Copy Blocks option selected.](/images/module-06/lesson-02/copy-pattern.png)

This will copy the block HTML code to your clipboard, allowing you to paste it where needed in your code editor.

## Register a Pattern via the /patterns Folder

The recommended method of registering a block pattern is by creating a new PHP file within a `/patterns` folder in your theme.  It's best to give it a filename that matches your pattern.  In this case, that would be `hero.php`.  

Create this file in your theme so that your theme structure looks like the following:

- `themeslug`
	- `/patterns`
		- `/hero.php`
	- `/...`

Patterns registered via the `/patterns` folder require a file header with the pattern data.  At the very least, each file requires a `Title` and `Slug` field.  A `Categories` field is strongly recommended too so that it's easier for users to find patterns related to what they're looking for.

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

> **Note** The `Slug` field should be namespaced based on your theme folder name.  So, if your theme's slug is `super-duper`, your `Slug` value becomes `super-duper/hero`.

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
Save your progress in your code editor.  Now, open a new post or page in the WordPress admin and click the **+** (Toggle block inserter) button in the editor.  Then, select the **Patterns** tab.  You should see your Hero pattern listed under the **Featured** category, as shown in the following screenshot:

![WordPress post editor with an empty content canvas and a left sidebar panel showing a list of patterns.](/images/module-06/lesson-02/pattern-in-inserter.jpg)

## Register a Pattern via functions.php

While it is not the recommended method, you can also register block patterns via the [`register_block_pattern()`](https://developer.wordpress.org/reference/functions/register_block_pattern/) function in your theme's `functions.php` file.  Generally, this method is more useful in plugins, which do not have the `/patterns` folder support as described earlier.

Here is an example code snippet of registering the Hero pattern you've already created via PHP:

```php
add_action( 'init', 'themeslug_register_patterns' );

function themeslug_register_patterns() {
	register_block_pattern( 'themeslug/hero', array(
		'title'      => __( 'Hero', 'themeslug' ),
		'categories' => array( 'featured' ),
		'content'    => '<!-- Block pattern goes here. -->'
	) );
}
```

The fields are the same as outlined earlier.  However, there are some key differences:

- Each field/key should be lowercase (e.g., `Title` becomes `title`).
- Comma-separated items, such as `categories`, should be listed within an `array()`.
- There is a `content` field for adding the block pattern content.

Within themes, there is little reason to use this method, but it is included here for completeness.

## Register a Pattern Category

By default, WordPress registers several pattern categories.  You can add one or more of these to your `Categories` field when registering a new block pattern:

- `buttons`
- `columns`
- `featured`
- `footer`
- `gallery`
- `header`
- `text`
- `query`

However, there are times when you may want to add custom categories for your theme's patterns.  Sometimes, none of the core categories make a good fit for what you've created.  At other times, you may want to separate your patterns from those registered by WordPress and third-party plugins.

One common category that themes add is a catchall group for all of their theme's patterns.  Let's create that via the `[register_block_pattern_category()](https://developer.wordpress.org/reference/functions/register_block_pattern_category/) function.

Open your theme's `functions.php` file in your code editor and enter the following code:

```php
add_action( 'init', 'themeslug_register_pattern_categories' );

function themeslug_register_pattern_categories() {
	register_block_pattern_category( 'themeslug', array( 
		'label' => __( 'Theme Name', 'themeslug' )
	) );
}
```

Change `themeslug` and `Theme Name` to your theme's real slug and name.

Now, open your original `/patterns/hero.php` file.  In the `Categories` header field, add your custom category to the list:

```php
<?php
/**
 * Title: Hero
 * Slug: themeslug/hero
 * Categories: featured, themeslug
 */
```

If you open the pattern inserter on the post-editing screen in the WordPress admin, you should now see your new category with your pattern listed under it:

![WordPress post editor with an empty content canvas and a left sidebar panel showing a custom category with a single Hero pattern.](/images/module-06/lesson-02/pattern-category.jpg)

## Unregister Patterns

There are times when you may desire to remove a registered block pattern.  Some scenarios include:

- A third-party plugin registering custom patterns
- A parent theme's patterns via a child theme
- WordPress' built-in patterns
- Remote patterns pulled from the [Pattern Directory](https://wordpress.org/patterns)

In any scenario, you can unregister a pattern as long as you know its name.  For example, if the pattern name is `pluginslug/awesome-pricing-table`, you would unregister it as shown in the following `functions.php` code snippet via the [`unregister_block_pattern()`](https://developer.wordpress.org/reference/functions/unregister_block_pattern/) function:

```php
add_action( 'init', 'themeslug_unregister_patterns', 15 );

function themeslug_unregister_patterns() {
	unregister_block_pattern( 'pluginslug/awesome-pricing-table' );
}
```

Note the priority of `15` in the `add_action()` call.  It's generally good practice to bump that number up above the default of `10` to make sure your function runs after registration functions from others.

It is not always the case that you will know the pattern name.  When WordPress loads remote patterns from the Pattern Directory, the patterns included will change over time.  If you attempt to unregister them by name, you will forever be playing catchup.  The good news is that WordPress provides a simple filter hook that allows you to disable them.

If you add the following single line of code to your `functions.php` file, it will disable all remote patterns:

```php
add_filter( 'should_load_remote_block_patterns', '__return_false' );
```

WordPress also includes a handful of patterns of its own.  It's possible to unregister these individually, but there's no way of knowing if more will be bundled in the future.  Themes can opt-out of supporting these via the `core-block-patterns` support flag.  

To fully remove support for all core patterns, add the following code to your theme's `functions.php` file:

```php
add_action( 'after_setup_theme', 'themslug_setup_patterns' );

function themeslug_setup_patterns() {
	remove_theme_support( 'core-block-patterns' );
}
```

> **Note** Removing core pattern support will also remove all remote patterns from the Pattern Directory.  This means that you do not need to filter  `should_load_remote_block_patterns` in this scenario.
