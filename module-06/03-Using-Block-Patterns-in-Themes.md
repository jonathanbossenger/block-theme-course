# Using Block Patterns in Themes

You learned how to register patterns in themes during the previous lesson.  That provides end-users with an easy method of inserting a pattern into their posts, pages, or custom templates via the site editor.  However, there is much more that you can do with the feature.

In this lesson, you will learn a few methods for using block patterns in your theme.  This will include using them within block templates, internationalizing text strings, and including dynamic data, such as a URL path to an image. 

## Using Patterns in Templates

WordPress allows theme authors to include a pattern directly in a block template or template part.  There are two primary reasons for this:

- **Reusability:** To follow the DRY (Don't Repeat Yourself) principle, reusing a pattern in multiple places.
- **Dynamic Data:** To include dynamic data that would otherwise be inaccessible in HTML-based templates and template parts.

You may be asking how you are supposed to use PHP-based patterns within HTML.  This is possible via WordPress' built-in Pattern block, a wrapper block for outputting individual patterns.

Let's say you have a `templates/home.html` template for your theme.  It might looks something like the following:

```html
<!-- wp:template-part {"slug":"header"} /-->

<!-- Some other blocks. /-->

<!-- wp:template-part {"slug":"footer"} /-->
```

However, you want to include your registered Hero pattern from the previous lesson just below the header.  To do this, you would use the Pattern block, which allows you to show a registered pattern in any block template or template part.

The Pattern block code looks like the following:

```html
<!-- wp:pattern {"slug":"namespace/slug"} /-->
```

Because you know the slug for your Hero pattern is `themeslug/hero`, all you need to do is pop that in and put the call to the Pattern block into your template.

Now, add that code to your `templates/home.html` template.  It should look similar to the following code snippet:

```html
<!-- wp:template-part {"slug":"header"} /-->

<!-- wp:pattern {"slug":"themeslug/hero"} /-->

<!-- Some other blocks. /-->

<!-- wp:template-part {"slug":"footer"} /-->
```

When a user loads the Home template via **Appearance > Editor**, they will see the pattern already placed into template:

![Hero pattern that stretches across the screen below a typical site title + menu header. It sits within the content canvas of the WordPress site editor.](/images/module-06/lesson-03/pattern-home-template-editor.jpg)

## Internationalizing Text in Patterns

When you built the Hero pattern, you added three different blocks with custom text.  Let's take a look at the Heading block from that pattern, the first to use such text:

```html
<h2 class="has-text-align-center">Welcome to My Site</h2>
```

The text string "Welcome to My Site" is problematic.  Not every user is a native speaker of the language you wrote that text in (English in this case).  When users insert patterns with custom text, it would be nice to see it in their own language.

The `<-- wp:pattern /-->` block was originally built as a method of internationalizing text strings.  This allows you to use translations functions, such as [`_e()` WordPress function](https://developer.wordpress.org/reference/functions/_e/), to make the text translatable.

The internationalized version of the Heading block should look like the following:

```php
<h2 class="has-text-align-center"><?php _e( 'Welcome to My Site', 'themeslug' ); ?></h2>
```

Now, follow this process for all three blocks with text strings in them.  Your `patterns/hero.php` file should now look similar to the following:

```php
<?php
/**
 * Title: Hero
 * Slug: themeslug/hero
 * Categories: featured, themeslug
 */
?>
<!-- wp:cover {"overlayColor":"contrast","align":"full"} -->
<div class="wp-block-cover alignfull"><span aria-hidden="true" class="wp-block-cover__background has-contrast-background-color has-background-dim-100 has-background-dim"></span><div class="wp-block-cover__inner-container"><!-- wp:group {"style":{"spacing":{"blockGap":"2.5rem"}},"layout":{"type":"constrained","wideSize":"%","contentSize":"75%"}} -->
<div class="wp-block-group"><!-- wp:heading {"textAlign":"center"} -->
<h2 class="has-text-align-center"><?php _e( 'Welcome to My Site', 'themeslug' ); ?></h2>
<!-- /wp:heading -->

<!-- wp:paragraph {"align":"center"} -->
<p class="has-text-align-center"><?php _e( "This is my little home away from home. Here, you will get to know me.  I'll share my likes, hobbies, and more.  Every now and then, I'll even have something interesting to say in a blog post.", 'themeslug' ); ?></p>
<!-- /wp:paragraph -->

<!-- wp:buttons {"layout":{"type":"flex","justifyContent":"center"}} -->
<div class="wp-block-buttons"><!-- wp:button {"className":"is-style-outline"} -->
<div class="wp-block-button is-style-outline"><a class="wp-block-button__link wp-element-button"><?php _e( 'See My Popular Posts →', 'themeslug' ); ?></a></div>
<!-- /wp:button --></div>
<!-- /wp:buttons --></div>
<!-- /wp:group --></div></div>
<!-- /wp:cover -->
```

## Adding Images and Other Dynamic Data in Patterns

Where patterns can be fun and exciting, offering a ton of flexibility is including other dynamic data.

Find an image on [WordPress Photos](https://wordpress.org/photos/), such as [night view of a hill area](https://wordpress.org/photos/photo/67563182d4/).

![WordPress post editor with a "hero" pattern in the content canvas. The pattern has a background image of the night sky with hills below it.](/images/module-06/lesson-03/hero-pattern-with-background.jpg)

Here is a partial view of what the Cover block code looks like with the included background image.  Take note of the two instances of the image URL that begin with `http://`:

```php
<!-- wp:cover {"url":"http://localhost/wp-content/uploads/2022/10/67563182d40242c84.99466282-2048x1152-jpg.webp","id":3424,"dimRatio":50,"overlayColor":"contrast","align":"full"} -->
<div class="wp-block-cover alignfull"><span aria-hidden="true" class="wp-block-cover__background has-contrast-background-color has-background-dim"></span><img class="wp-block-cover__image-background wp-image-3424" alt="" src="http://localhost/wp/wp-content/uploads/2022/10/67563182d40242c84.99466282-2048x1152-jpg.webp" data-object-fit="cover"/>
```

Just like the plain text strings covered in the previous section, if you build this pattern directly from the editor, your image URL will be static and look something like `http://localhost/wp-content/2022/10/image-name.webp`.  That is problematic because the URL is specific to the URL of the install where you built the pattern.  Therefore, you must include it dynamically.

To bundle it in the theme, first give the image a easy-to-remember filename, such as `hero-background.webp`.  Then, add it to your theme's `/assets/images` folder (create this if it doesn't already exist).  Your theme's directory structure should look like the following:

- `themeslug`
	- `/assets`
		- `/images`
			- `/hero-background.webp`

Now, you must replace each of the image URL paths in the `patterns/hero.php` file with a reference to the file in your theme.  You will do this with the `get_theme_file_uri()` function.  And, to be on the safe side, you will wrap it in `esc_url()` to make sure it is escaped and prevent any potential security issues.

Make sure you replace both instances of the URL string, which should look like:

```
http://localhost/wp-content/2022/10/image-name.webp
```

With:

```php
<?php echo esc_url( get_theme_file_uri( 'assets/images/hero-background.webp' ) ); ?>
```

Once you've replaced each instance of the URL path, your `patterns/hero.php` file should look like the following:

```php
<?php
/**
 * Title: Hero
 * Slug: themeslug/hero
 * Categories: featured, themeslug
 */
?>
<!-- wp:cover {"url":"<?php echo esc_url( get_theme_file_uri( 'assets/images/hero-background.webp' ) ); ?>","id":3424,"dimRatio":50,"overlayColor":"contrast","align":"full"} -->
<div class="wp-block-cover alignfull"><span aria-hidden="true" class="wp-block-cover__background has-contrast-background-color has-background-dim"></span><img class="wp-block-cover__image-background wp-image-3424" alt="" src="<?php echo esc_url( get_theme_file_uri( 'assets/images/hero-background.webp' ) ); ?>" data-object-fit="cover"/><div class="wp-block-cover__inner-container"><!-- wp:group {"style":{"spacing":{"blockGap":"2.5rem"}},"layout":{"type":"constrained","wideSize":"%","contentSize":"75%","justifyContent":"center"}} -->
<div class="wp-block-group"><!-- wp:heading {"textAlign":"center"} -->
<h2 class="has-text-align-center">Welcome to My Site</h2>
<!-- /wp:heading -->

<!-- wp:paragraph {"align":"center"} -->
<p class="has-text-align-center"><?php _e( "This is my little home away from home. Here, you will get to know me.  I'll share my likes, hobbies, and more.  Every now and then, I'll even have something interesting to say in a blog post.", 'themeslug' ); ?></p>
<!-- /wp:paragraph -->

<!-- wp:buttons {"layout":{"type":"flex","justifyContent":"center"}} -->
<div class="wp-block-buttons"><!-- wp:button {"className":"is-style-outline"} -->
<div class="wp-block-button is-style-outline"><a class="wp-block-button__link wp-element-button"><?php _e( 'See My Popular Posts →', 'themeslug' ); ?></a></div>
<!-- /wp:button --></div>
<!-- /wp:buttons --></div>
<!-- /wp:group --></div></div>
<!-- /wp:cover -->
```

Once you saved your progress, go to **Pages > Add New** in your WordPress admin and open the pattern inserter.  Your new pattern with its background image should appear:

![WordPress page editor with the Patterns inserter open on the left, showing a single hero pattern with a background image.](/images/module-06/lesson-03/hero-with-background-inserter.jpg)

> **Note**\
> Dynamic data only remains dynamic when it comes from the theme.  The moment that a user saves a post in the block content editor or a template in the site editor, the data becomes static.  You cannot later update that specific instance of the pattern.

Images are merely the tip of the iceberg when it comes to what type of data you can use in a block pattern.  You could potentially show a specific configuration of a pattern based on whether a specific plugin is active, for example.  Internationalizing text strings and including media are the most common scenarios.

> **Note**\
> Because patterns are registered on the `init` action hook, they cannot rely on any data or conditionals that are set or generated after that point in the WordPress load process.
