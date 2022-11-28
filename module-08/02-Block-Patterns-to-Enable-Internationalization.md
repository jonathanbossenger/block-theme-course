# Using Block Patterns to Enable Internationalization

As you leaned in module x of this course, Block Patterns are a way that you can implement PHP code in a block theme. In the section on Adding Images and Other Dynamic Data in Patterns, you used a PHP function to add a hero image to the pattern.


```php
echo esc_url( get_theme_file_uri( 'assets/images/hero-background.webp' ) ); 
```

This means that you can make use of the same PHP support in patterns, and start making any theme text translatable.

## Creating a translatable footer

In this lesson, you're going to make the text that appears in the footer of your block theme translatable. Let's take a look at that template in the Site Editor

> **Do**
> 1. Open the Site Editor, and navigate to the list of template parts.
> 2. Open the Footer template part

![Footer template part](https://learn.wordpress.org/files/2022/11/footer-template-part.png)

If you switch to the Code Editor view, or view footer.html file contents, the block code that makes up the footer looks like this:

```html
<!-- wp:group {"style":{"spacing":{"padding":{"top":"var(--wp--preset--spacing--90)"}}},"layout":{"inherit":true}} -->
<div class="wp-block-group" style="padding-top:var(--wp--preset--spacing--90)"><!-- wp:group {"align":"wide","style":{"spacing":{"padding":{"top":"var(--wp--preset--spacing--90)","bottom":"var(--wp--preset--spacing--90)"}}},"layout":{"type":"flex","justifyContent":"space-between"}} -->
    <div class="wp-block-group alignwide" style="padding-top:var(--wp--preset--spacing--90);padding-bottom:var(--wp--preset--spacing--90)"><!-- wp:site-title {"level":0} /-->
        <!-- wp:paragraph {"align":"right"} -->
        <p class="has-text-align-right">Proudly powered by <a href="https://wordpress.org" rel="nofollow">WordPress</a></p>
        <!-- /wp:paragraph --></div>
    <!-- /wp:group --></div>
<!-- /wp:group -->
```

In that footer code, the "Proudly powered by" text can be made translatable by wrapping it in a translation function. To keep things simple, we'll use the same __() function you saw in the previous lesson.

### Creating the initial pattern

The first step is to take the section of block markup that contains the text you want to translate, and move it to a pattern. In this case we'll use a pattern file in the theme, which needs to be created in the `patterns` directory. The entire wp:paragraph block should be moved, so start by copying the code to a new pattern.

> **Do**
> Copy the wp:paragraph block from the footer template part, and paste it into a new pattern file in the `patterns` directory called `footer-powered-by.php`

Next, add the block pattern header. In this instance you only have to supply the Title and Slug fields, as you don't need the pattern to show up in the inserter.

```php
<?php
/**
 * Title: Powered by pattern
 * Slug: block-course-theme/powered-by
 */
?>
```
>  **Do**
> Add the header comment to the pattern, above the block pattern code.

Your final pattern file should look like this:

```php
<?php
/**
 * Title: Powered by pattern
 * Slug: block-course-theme/powered-by
 */
?>
<!-- wp:paragraph {"align":"right"} -->
    <p class="has-text-align-right">Proudly powered by <a href="https://wordpress.org" rel="nofollow">WordPress</a></p>
<!-- /wp:paragraph -->
```

Now you can update the footer.html file, and replace the code you copied out with the pattern block by passing in the pattern slug.

```html
<!-- wp:pattern {"slug":"block-course-theme/powered-by"} /-->
```

> **Do**
> Update the footer.html template part to use the newly created pattern

Here's what the footer template part should look like once you've updated it.

```html
<!-- wp:group {"style":{"spacing":{"padding":{"top":"var(--wp--preset--spacing--90)"}}},"layout":{"inherit":true}} -->
<div class="wp-block-group" style="padding-top:var(--wp--preset--spacing--90)"><!-- wp:group {"align":"wide","style":{"spacing":{"padding":{"top":"var(--wp--preset--spacing--90)","bottom":"var(--wp--preset--spacing--90)"}}},"layout":{"type":"flex","justifyContent":"space-between"}} -->
    <div class="wp-block-group alignwide" style="padding-top:var(--wp--preset--spacing--90);padding-bottom:var(--wp--preset--spacing--90)"><!-- wp:site-title {"level":0} /-->
        <!-- wp:pattern {"slug":"block-course-theme/powered-by"} /-->
    </div>
    <!-- /wp:group --></div>
<!-- /wp:group -->
```

If you refresh the Site Editor in WordPress, it should look the same, as the code for the pattern is automatically included in the footer template part.

### Apply the Translation Function

Now you can make the "Proudly powered by" text translatable, by applying the translation function to it. 

> **Do**
> 1. Wrap the text you want to make translatable in the __() function
> 2. Make sure the text is inside quotes, and you pass the text domain as the second parameter
> 3. Include an echo statement to output the translated text
> 4. Wrap the code in a PHP block

The text domain is the same value that you used in the style.css file, so you can use that here.

```php
<?php echo __('Proudly powered by', 'new-blank-theme'); ?>
```

The final pattern code looks like this:

```php
/**
 * Title: Powered by pattern
 * Slug: block-course-theme/powered-by
 */
?>
<!-- wp:paragraph {"align":"right"} -->
    <p class="has-text-align-right"><?php echo __('Proudly powered by', 'new-blank-theme'); ?> <a href="https://wordpress.org" rel="nofollow">WordPress</a></p>
<!-- /wp:paragraph -->
```

## Internationalizing the Hero Pattern

Remember the Hero pattern you built in module 6. That pattern included some human-readable text that could do with internationalizing. 

The first section you could update would be the Heading block from that pattern:

```html
<h2 class="has-text-align-center">Welcome to My Site</h2>
```

The internationalized version of the Heading block should look like the following:

```php
<h2 class="has-text-align-center"><?php _e( 'Welcome to My Site', 'themeslug' ); ?></h2>
```

> **Tip:** the _e function is a wrapper for "echo __()" so it in can be used to quickly make a string translatable, and echo it to the screen.

> **Do:** Now, follow this process for all three blocks with text strings in them.  Your `patterns/hero.php` file should now look similar to the following:

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

> **Note** Dynamic data, such as internationalized text strings, only remains dynamic when it comes from the theme.  The moment that a user saves a post in the block content editor or a template in the site editor, the data becomes static.

