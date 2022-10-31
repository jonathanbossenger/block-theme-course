# Creating Block Patterns

Block patterns are one of the most powerful and versatile APIs at a theme author's disposal.  Introduced in WordPress 5.4, patterns made it easier for users to insert more complex layouts from the block editor while opening a world of possibilities to designers.

## What Is a Block Pattern?

At its foundation, a block pattern is nothing more than one or more blocks that have been pre-configured and presented to the end-user.  The user can then insert it into the content, template, or site editor.  Then, configure it to their desired look.

You can bundle these directly into a theme.  The following is a screenshot of some Gallery patterns:

![Gallery patterns as shown in the WordPress pattern modal.](/images/module-06/lesson-01/gallery-patterns.jpg)

You can also submit them to the [Pattern Directory](https://wordpress.org/patterns/) and make them available to all WordPress users:

![Screenshot of the WordPress.org Pattern Directory, which shows a grid of block patterns](/images/module-06/lesson-01/pattern-directory.jpg)

Patterns can pretty much be anything.  They can be as simple as a single Gallery block with some preset options for the user.  They can be something extremely complex, such as a full page layout for a magazine-type website.  Or, something in between, such as a product pricing table.

What you build is only limited by your imagination and what the block editor is capable of.  With that in mind, let's start building a block pattern

## Designing a Pattern from the Block Editor

Building a custom block pattern requires no special skills or coding knowledge.  As mentioned earlier, a pattern is merely a pre-configured set of blocks.  Therefore, anyone with access to the WordPress editor can build one.

For this exercise, let's build one of the more common layouts from around the web:  the hero pattern.

There are many forms this pattern can take, but at its most basic level, it is typically a full-width box with a background that contains some text.  Often, this is a heading, paragraph, and some buttons.

To get started, visit your WordPress admin area and click on **Pages > Add New**.  Then, insert a Cover block into the empty canvas, as shown in the following screenshot, and choose a background color:

![WordPress page editor with an empty Cover block in the content area, prompting the user to pick a color.](/images/module-06/lesson-01/hero-header-step-01.jpg)

The exciting part about creating a block pattern is that you get to build it however you want.  You are the designer, so now is the time to explore what is possible.

For the hero pattern, try recreating the following content within your inserted Cover block.  _Hint: it contains a Group block, which contains Heading, Paragraph, and Buttons blocks._

![WordPress page editor with a hero header, containing a heading, paragraph, and button.](/images/module-06/lesson-01/hero-header-step-02.jpg)

If you run into any trouble, copy the following block HTML code and insert it into the editor.  Then, feel free to customize it.

```html
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

Congratulations! You have now successfully created a custom block pattern.  Of course, there's not much you can do with it other than customize it from the editor at this point.  In the upcoming lesson, you will learn how to register and bundle it with your theme.