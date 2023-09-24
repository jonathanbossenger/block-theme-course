# Block Theme Templates

[Supplemental Video](https://videopress.com/v/S6ufFSi2)

The core files that make up a WordPress theme are templates. [Templates](https://developer.wordpress.org/themes/basics/template-files/) are the files that WordPress uses to render the content of a post or page. 

In a classic theme templates are PHP files that contain HTML and PHP code. In a block theme, templates are HTML files that contain HTML and block markup. Both classic and block theme templates follow the WordPress [Template Hierarchy](https://developer.wordpress.org/themes/basics/template-hierarchy/).

The Template Hierarchy is the logic WordPress uses to decide which theme template file to use when rendering content. By creating template files that follow the Template Hierarchy naming convention WordPress can automatically determine which template file to use for a given piece of content.

For example, to render the content for a single post, you can create any of the [single post template files](https://developer.wordpress.org/themes/basics/template-hierarchy/#single-post), and WordPress will use the first one it finds in the theme directory. 

## Editing or Creating Templates

One of the main advantages of block themes over classic themes is that you can edit existing templates or create new theme templates from the Site Editor. 

This is useful when developing themes, as you could use a "base" or "starter" block theme, edit the base templates, and then export the updated templates to a new theme. Alternatively, you could create an entirely new theme from scratch for a specific use case, all from the Site Editor. 

> **Note:** For a full breakdown of all the different parts of the Site Editor, take a look at this [detailed overview of the Site Editor](https://wordpress.org/support/article/site-editor/).

You can then either save the template for the current site, which stores it in the database, or export the template code into the relevant file in the `templates` directory of your theme. 

### Adding Content to the index.html Template

In the previous lesson, you created an empty `index.html` template file. Let's add some content to this template.

Start by navigating to Appearance -> Editor. The Site Editor will open and after clicking anywhere on the blank canvas, you will be ready to add content to your index.html template.

![The index template in the editor](https://learn.wordpress.org/files/2022/10/empty-index-template.png)

As the index template is the default template that WordPress will load if it can't find a matching template file for the content being rendered, it's a good idea to add some content to this template. General best practice is to populate this template with a query loop, so that all posts on the site are displayed.

> **Note:** The Query Loop block is equivalent to [The Loop](https://codex.wordpress.org/The_Loop) in a classic theme. For more details on the power of the Query Loop block, take a look at this [tutorial](https://learn.wordpress.org/tutorial/taking-advantage-of-query-loops/).

While editing your template, you can toggle the Site Editor's List View to get a better overview of the template's structure, and select specific blocks.

![Enabling the List View](https://learn.wordpress.org/files/2022/10/enabling-list-view.png)

Go ahead and add a query loop to the template, the pagination block, and a spacer to allow a bit of space between the query loop and the pagination.

> **Do:** 
> 1. Add a **Query Loop** block, select **Choose** then select the **Standard** pattern for the block.
> 2. Add a **Pagination** block inside the **Query Loop**, right at the bottom, after the **Post Template** block.
> 3. Inside the **Query Loop**, add a **Spacer** block at the bottom of the **Post Template** block.

![The index template with a header and query loop](https://learn.wordpress.org/files/2022/10/basic-index-template.png)

If you switch to the Code editor View, you'll be able to see the block markup for the Query Loop block.

> **Do:** Enable the Code editor view by clicking the More Options three-dot menu and selecting **Code editor**.

> ![Enabling the Code editor](https://learn.wordpress.org/files/2022/10/editor-more-options.png)

```
<!-- wp:query {"queryId":31,"query":{"perPage":3,"pages":0,"offset":0,"postType":"post","order":"desc","orderBy":"date","author":"","search":"","exclude":[],"sticky":"","inherit":true}} -->
<div class="wp-block-query"><!-- wp:post-template -->
<!-- wp:post-title {"isLink":true} /-->

<!-- wp:post-featured-image {"isLink":true,"align":"wide"} /-->

<!-- wp:post-excerpt /-->

<!-- wp:separator {"opacity":"css"} -->
<hr class="wp-block-separator has-css-opacity"/>
<!-- /wp:separator -->

<!-- wp:post-date /-->

<!-- wp:spacer -->
<div style="height:100px" aria-hidden="true" class="wp-block-spacer"></div>
<!-- /wp:spacer -->
<!-- /wp:post-template -->

<!-- wp:query-pagination -->
<!-- wp:query-pagination-previous /-->

<!-- wp:query-pagination-numbers /-->

<!-- wp:query-pagination-next /-->
<!-- /wp:query-pagination --></div>
<!-- /wp:query -->
```

> **Do:** Remember to exit the Code editor when you're done looking at the code! 

If you save this template content, it will save the changes to the database. This means the template structure will only be available for this site. In lesson 4 of this module we'll review how to export the code to a template file. 

> **Do:** Save this template now, we'll export it in a bit!

### Adding New Templates from the Site Editor

Besides adding block content to existing templates, you can also create brand new templates from the Site Editor. 

To start from within the Site Editor, click on the **Open Navigation** button in the top left corner of your screen.

Navigate back to Templates then click on the **Add New Template** plus sign icon.

![Editor Navigation](https://learn.wordpress.org/files/2022/10/editor-navigation.png)

Alternatively, you can select **Manage all templates** where you'll be presented with a list of the templates in this theme, and a button to add a new template.

![Editor Templates](https://learn.wordpress.org/files/2022/10/editor-templates.png)

![Editor Add new template](https://learn.wordpress.org/files/2022/10/editor-add-new-template.png)

The Editor will give you the option of creating a new template based on the primary templates, ranging from things like a Front Page to a 404 Page. 

**NEW SCREENSHOT GOES HERE editor-add-new-template-popup.png**

> **Do:** 
> 1. Select the **Pages** option, to create a new page template.
> 2. Select **All Pages** to create a template that will be used for all pages.
> 3. Don't choose the pattern and instead click **Skip** to start from scratch.

The page template will be created, and you'll be taken to the editor to add blocks to the template. Note that the pattern you were presented with was automatically populated with the content from the index template.

Because a page in WordPress is merely a custom post type, you can use the **Post Title, Post Featured Image**, and **Post Content** blocks to render the title and content of a page in the template. You can also use **Group** blocks to logically group specific blocks, based on the design.

> **Do:**
> 1. Add a **Group** block to the template.
> 2. Add another **Group** block nested below.
> 3. Add a **Post Featured Image** block and the **Title** block to the nested Group block.
> 4. Add a **Post Content** block below the nested Group block.

Your final page template should look something like this:

![Image of the page template](https://learn.wordpress.org/files/2022/10/page-template.png)

Now switch to the Code editor view, to see the block markup that makes up this page template.

```html
<!-- wp:group {"layout":{"type":"constrained"}} -->
<div class="wp-block-group"><!-- wp:group {"layout":{"type":"constrained"}} -->
    <div class="wp-block-group"><!-- wp:post-featured-image /-->

        <!-- wp:post-title /--></div>
    <!-- /wp:group -->

    <!-- wp:post-content /--></div>
<!-- /wp:group -->
```

Finally, remember to exit the Code editor view, and save the template.

> **Do:** Save this template now, so it's included when we export it later!

### Further Reading

You can read more about the [block theme templates](https://developer.wordpress.org/themes/block-themes/templates-and-template-parts/) in the Theme Handbook. If you're interested in reading up about all the core blocks available in the Site Editor, the Theme Developer Handbook has this handy list of [all core blocks](https://developer.wordpress.org/block-editor/reference-guides/core-blocks/).

Now that we've covered theme templates, let's take a look at template parts.