# Locking Blocks to Prevent User Changes

The WordPress Locking API is a feature for locking down the state of blocks and preventing end-users from changing specific aspects about them.  There are many reasons for doing this, such as keeping a client from overwriting branding elements or a user from rearranging a set of blocks that are vital to the overall design.

Parts of the Locking API are available directly via the editor, so theme authors can build out their templates and patterns from the comfort of the interface.

> **Do:** For the purposes of this lesson, you will build an initial pattern of blocks to work with.  The layout can be anything, but try recreating the following full-width Group and its nested blocks:

![WordPress content editor with a full-width Group block and purple background. Nested inside are Heading, Paragraph, and Button blocks in white demo text.](https://learn.wordpress.org/files/2022/11/locking-base-pattern.png)

The pattern contains the following blocks, arranged like so:

- Group
	- Heading
	- Paragraph
	- Buttons

The following code snippet is the block code if you get stuck. It will give you a base pattern to work with as you make your way through the remainder of this lesson.

```html
<!-- wp:group {"align":"full","style":{"spacing":{"blockGap":"32px","padding":{"top":"128px","bottom":"128px"}}},"backgroundColor":"vivid-purple","textColor":"white","layout":{"type":"constrained"}} -->
<div class="wp-block-group alignfull has-white-color has-vivid-purple-background-color has-text-color has-background" style="padding-top:128px;padding-bottom:128px"><!-- wp:heading {"textColor":"base"} -->
<h2 class="has-base-color has-text-color">WordCamp Happiness Bar</h2>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>Please treat yourself, join in on the fun this year, and stop by the happiness bar.</p>
<!-- /wp:paragraph -->

<!-- wp:buttons -->
<div class="wp-block-buttons"><!-- wp:button {"className":"is-style-outline"} -->
<div class="wp-block-button is-style-outline"><a class="wp-block-button__link wp-element-button">See Schedule</a></div>
<!-- /wp:button --></div>
<!-- /wp:buttons --></div>
<!-- /wp:group -->
```

## Lock Specific Blocks in Place

With your base set of blocks in place in the editor, you will now learn how to lock them down.  WordPress provides several locking options directly via the block editor UI.

> **Do:** Select the Group block in the content canvas and click the **⋮** (Options) button in the toolbar.  Look for the option titled **Lock**, as shown in the following screenshot:

![Dropdown options list in the WordPress post editor toolbar. The "Lock" option is highlighted in the list.](https://learn.wordpress.org/files/2022/11/locking-dropdown.png)

Once you click the **Lock** option, a popup modal will appear over the editor with the settings shown in the following screenshot:

![WordPress post editor with a popup modal that shows a list of options for locking the selected Group block.](https://learn.wordpress.org/files/2022/11/locking-popup.png)

Each option applies a specific locking mechanism to the block itself and/or its children:

- **Lock all:** Catchall for both of its sub-options:
	- **Disable movement:** Disallows users from moving the block within the editor (doesn't disallow movement of sibling blocks).
	- **Prevent removal:** Prevents users from removing the block altogether.
- **Apply to all blocks inside:** Applies the rules selected to all nested blocks.

> **Note** As you can see, the ability to lock blocks is available directly via the interface. This also means the ability to **unlock** blocks is also available to users.  From a practical standpoint, locking blocks in themes merely helps prevent accidental movement and removal in complex layouts.  It is possible to [build custom permissions](https://developer.wordpress.org/block-editor/how-to-guides/curating-the-editor-experience/#locking-apis) around the locking API.  However, that is outside of the scope of this theme course.

If you select each of the individual options, you will lock the entire Group block down, preventing it from being moved or removed.  The following snippet is what the code should look like.  You can copy and paste it directly into a custom pattern or theme template.

```php
<!-- wp:group {"templateLock":"all","lock":{"move":true,"remove":true},"align":"full","style":{"spacing":{"blockGap":"32px","padding":{"top":"128px","bottom":"128px"}}},"backgroundColor":"vivid-purple","textColor":"white","layout":{"type":"constrained"}} -->
<div class="wp-block-group alignfull has-white-color has-vivid-purple-background-color has-text-color has-background" style="padding-top:128px;padding-bottom:128px"><!-- wp:heading {"textColor":"base"} -->
<h2 class="has-base-color has-text-color">WordCamp Happiness Bar</h2>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>Please treat yourself, join in on the fun this year, and stop by the happiness bar.</p>
<!-- /wp:paragraph -->

<!-- wp:buttons -->
<div class="wp-block-buttons"><!-- wp:button {"className":"is-style-outline"} -->
<div class="wp-block-button is-style-outline"><a class="wp-block-button__link wp-element-button">See Schedule</a></div>
<!-- /wp:button --></div>
<!-- /wp:buttons --></div>
<!-- /wp:group -->
```

## "Content-Only" Editing (Design Locking)

Content-only editing doesn't sound like a part of the Locking API at first glance.  A better name for the locking aspect of it is "design locking."  Essentially, it allows theme authors to lock down the design tools of the block itself and any inner blocks.  From the user's perspective, they can edit just the content (i.e., text, images, and other media).

The core blocks that support content locking are limited to Group, Cover, and Column.  These are the major container-type blocks that house smaller pieces of a layout.

Unlike the other locking methods, this cannot be configured through the editor interface.  You must modify the block code directly.

Let's take the original base pattern's code you created earlier in this lesson.  The block comment code for the Group block should look similar to the following:

```html
<!-- wp:group {"align":"full","style":{"spacing":{"blockGap":"32px","padding":{"top":"128px","bottom":"128px"}}},"backgroundColor":"vivid-purple","textColor":"white","layout":{"type":"constrained"}} -->
```

> **Do:** To lock down the design and allow the end-user to only edit the content, you must add `"templateLock":"contentOnly"` within the comment's JSON.  Your code should look similar to the following:

```html
<!-- wp:group {"templateLock":"contentOnly","align":"full","style":{"spacing":{"blockGap":"32px","padding":{"top":"128px","bottom":"128px"}}},"backgroundColor":"vivid-purple","textColor":"white","layout":{"type":"constrained"}} -->
```

> **Do:** Now, turn this into a pattern by placing the code into a `patterns/happiness-bar.php` file in your theme.  Please refer back to the [Block Patterns Lesson](/module-06/01-Creating-a-Block-Pattern.md) if you need a refresher on registering custom patterns.

Your `patterns/happiness-bar.php` file should look like the following:

```php
<?php
/**
 * Title: Happiness Bar
 * Slug: themeslug/happiness-bar
 * Categories: featured
 */
?>
<!-- wp:group {"templateLock":"contentOnly","align":"full","style":{"spacing":{"blockGap":"32px","padding":{"top":"128px","bottom":"128px"}}},"backgroundColor":"vivid-purple","textColor":"white","layout":{"type":"constrained"}} -->
<div class="wp-block-group alignfull has-white-color has-vivid-purple-background-color has-text-color has-background" style="padding-top:128px;padding-bottom:128px"><!-- wp:heading {"textColor":"base"} -->
<h2 class="has-base-color has-text-color">WordCamp Happiness Bar</h2>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>Please treat yourself, join in on the fun this year, and stop by the happiness bar.</p>
<!-- /wp:paragraph -->

<!-- wp:buttons -->
<div class="wp-block-buttons"><!-- wp:button {"className":"is-style-outline"} -->
<div class="wp-block-button is-style-outline"><a class="wp-block-button__link wp-element-button">See Schedule</a></div>
<!-- /wp:button --></div>
<!-- /wp:buttons --></div>
<!-- /wp:group -->
```

Once you've saved the pattern to your theme, go to **Pages > Add New** in the WordPress admin and insert it.  If you select the Header, Paragraph, or Buttons blocks within the content canvas, you should see that none of them have any design tools attached to them in the toolbar or block inspector sidebar panel.  Instead, the sidebar shows the grouped blocks:

![WordPress content editor with a full-width Group block with a purple background. On the right, the nested blocks are shown in the sidebar in lieu of design tools.](https://learn.wordpress.org/files/2022/11/locking-content-only.png)

Locked patterns like this are crucial to creating a curated editing experience, especially as you begin applying locking to more complex layouts and in templates.  Imagine creating the perfect site header design, which may often be too advanced for a client to meddle with.  With the locking API, you can break down the editing process to just the important pieces, such as customizing nav menu links.

This lesson has barely scratched the surface of what is possible.  Take the time to experiment and explore, mixing and matching locking features within your theme.
