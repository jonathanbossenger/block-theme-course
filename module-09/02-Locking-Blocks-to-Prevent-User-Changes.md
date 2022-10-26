# Locking Blocks to Prevent User Changes

!! Opening Description Needed !!

---

Before moving forward, let's put what you've learned from the previous [Block Patterns Lesson](/module-06/01-Creating-a-Block-Pattern.md) to use.  The WordPress Locking API works best within patterns and templates.  For the purposes of this lesson, let's build a pattern.

The pattern can be anything, but try recreating the following Group pattern:

![](/images/module-09/lesson-02/locking-base-pattern.png)

It contains the following blocks, arranged like so:

- Group
	- Heading
	- Paragraph
	- Buttons

Then, register the pattern in the `patterns/happiness-bar.php` file in your theme.  The following code snippet is the full pattern code if you get stuck:

```php
<!-- wp:group {"align":"full","style":{"spacing":{"blockGap":"32px","padding":{"top":"128px","bottom":"128px"}}},"backgroundColor":"vivid-purple","textColor":"white","layout":{"type":"constrained"}} -->
<div class="wp-block-group alignfull has-white-color has-vivid-purple-background-color has-text-color has-background" style="padding-top:128px;padding-bottom:128px"><!-- wp:heading {"textColor":"base"} -->
<h2 class="has-base-color has-text-color">WordCamp Happiness Bar<span style="font-family: system-ui, 'Apple Color Emoji', 'Noto Color Emoji', EmojiNotoColor, 'Noto Emoji', EmojiNoto, 'Segoe UI', 'Segoe UI Emoji', 'Segoe UI Symbol', 'Twitter Color Emoji', EmojiTwemColor, 'Twemoji Mozilla', EmojiTwem, 'EmojiOne Mozilla', 'Android Emoji', EmojiSymbols, Symbola, EmojiSymb !important;"></span></h2>
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

This will give you a nice base pattern to work with as you make your way through the remainder of this lesson.

## Lock Specific Blocks in Place

```php
<!-- wp:group {"templateLock":"all","lock":{"move":true,"remove":true},"align":"full","style":{"spacing":{"blockGap":"32px","padding":{"top":"128px","bottom":"128px"}}},"backgroundColor":"vivid-purple","textColor":"white","layout":{"type":"constrained"}} -->
<div class="wp-block-group alignfull has-white-color has-vivid-purple-background-color has-text-color has-background" style="padding-top:128px;padding-bottom:128px"><!-- wp:heading {"textColor":"base"} -->
<h2 class="has-base-color has-text-color">WordCamp Happiness Bar<span style="font-family: system-ui, 'Apple Color Emoji', 'Noto Color Emoji', EmojiNotoColor, 'Noto Emoji', EmojiNoto, 'Segoe UI', 'Segoe UI Emoji', 'Segoe UI Symbol', 'Twitter Color Emoji', EmojiTwemColor, 'Twemoji Mozilla', EmojiTwem, 'EmojiOne Mozilla', 'Android Emoji', EmojiSymbols, Symbola, EmojiSymb !important;"></span></h2>
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

## Design Locking ("Content Only" Editing)

Content-only editing doesn't sound like a part of the Locking API at first glance.  A better name for the "locking" aspect of it is "design locking."  Essentially, it allows theme authors to lock down the design tools of the block itself and any inner blocks.  From the user's perspective, they 

The core blocks that support content locking are column, cover, and group.

```php
<!-- wp:group {"templateLock":"contentOnly","align":"full","style":{"spacing":{"blockGap":"32px","padding":{"top":"128px","bottom":"128px"}}},"backgroundColor":"vivid-purple","textColor":"white","layout":{"type":"constrained"}} -->
<div class="wp-block-group alignfull has-white-color has-vivid-purple-background-color has-text-color has-background" style="padding-top:128px;padding-bottom:128px"><!-- wp:heading {"textColor":"base"} -->
<h2 class="has-base-color has-text-color">WordCamp Happiness Bar<span style="font-family: system-ui, 'Apple Color Emoji', 'Noto Color Emoji', EmojiNotoColor, 'Noto Emoji', EmojiNoto, 'Segoe UI', 'Segoe UI Emoji', 'Segoe UI Symbol', 'Twitter Color Emoji', EmojiTwemColor, 'Twemoji Mozilla', EmojiTwem, 'EmojiOne Mozilla', 'Android Emoji', EmojiSymbols, Symbola, EmojiSymb !important;"></span></h2>
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
