# Block Theme Templates

[Short video covering this lesson]

The core files that make up a WordPress theme are templates. [Templates](https://developer.wordpress.org/themes/basics/template-files/) are the files that WordPress uses to render the content of a post or page. 

In a classic theme templates are PHP files that contain HTML and PHP code. In a block theme, templates are HTML files that contain HTML and block markup. Both classic and block theme templates follow the WordPress [Template Hierarchy](https://developer.wordpress.org/themes/basics/template-hierarchy/).

The Template Hierarchy is the logic WordPress uses to decide which theme template file to use when rendering content. By creating template files that follow the Template Hierarchy naming convention WordPress can automatically determine which template file to use for a given piece of content.

For example, to render the content for a single post, you can create any of the [single post template files](https://developer.wordpress.org/themes/basics/template-hierarchy/#single-post), and WordPress will use the first one it finds in the theme directory. 

## Editing or Creating Templates

One of the main advantages of block themes over classic themes, is that you can edit existing templates or create new theme templates from the Site editor. 

> For a detailed breakdown of all the different parts of the Site editor, take a look at this [handy help document](https://wordpress.org/support/article/site-editor/).

You can then either save the template for the current site, which stores it in the database, or export the template code into the relevant file in the `templates` directory of your theme. 

### Adding Content to the index.html Template

In the last lesson, you create an empty `index.html` template file. Let's add some content to this template.

Start by navigating to Appearance -> Editor. You'll be presented with a blank canvas, ready to add content to your index.html template.

![The index template in the editor](/images/module-02/empty-index-template.png)

As the index template is the default template that WordPress will load if it can't find a matching template file for the content being rendered, it's a good idea to add some content to this template. General best practice is to populate this template with a query loop, so that all posts on the site are displayed.

> 1. Add a heading block, and give the template a heading
> 2. Add a query loop block, and select the **Standard** pattern for the query loop.

![The index template with a header and query loop](/images/module-02/basic-index-template.png)

If you switch to the Code editor View, you'll be able to see the block markup for the heading and query loop blocks.

> Enable the Code editor view by clicking the More Options three-dot menu and selecting **Code editor**.
> ![Enabling the Code editor](/images/module-02/editor-more-options.png)

```
<!-- wp:heading -->
<h2>Site Index</h2>
<!-- /wp:heading -->

<!-- wp:query {"queryId":9,"query":{"perPage":3,"pages":0,"offset":0,"postType":"post","order":"desc","orderBy":"date","author":"","search":"","exclude":[],"sticky":"","inherit":false}} -->
<div class="wp-block-query"><!-- wp:post-template -->
<!-- wp:post-title {"isLink":true} /-->

<!-- wp:post-featured-image {"isLink":true,"align":"wide"} /-->

<!-- wp:post-excerpt /-->

<!-- wp:separator {"opacity":"css"} -->
<hr class="wp-block-separator has-css-opacity"/>
<!-- /wp:separator -->

<!-- wp:post-date /-->
<!-- /wp:post-template --></div>
<!-- /wp:query -->
```

> Remember to exit the Code editor when you're done looking at the code! 

If you save this template content, it will save the changes to the database. This means the template structure will only be available for this site. In lesson 4 of this module we'll review how to export the code to a template file. 

> Save this template now, we'll export it in a bit!

### Adding New Templates from the Site Editor

Besides adding block content to existing templates, you can also create brand new templates from the Site editor. 

To start, toggle to the Site editor navigation sidebar, and click on "Templates" in the editor navigation.

> If you don't see the Site editor navigation sidebar, click the WordPress logo in the top left corner of the editor, which is the  "Toggle Navigation" button.

![Editor Navigation](/images/module-02/editor-navigation.png)

You'll be presented with a list of the templates in this theme, and a button to add a new template.

![Editor Templates](/images/module-02/editor-templates.png)

> Click on the Add New button to create a new template.

![Editor Add new template](/images/module-02/editor-add-new-template.png)

The Editor will give you the option of creating a new template based on the primary templates, ranging from things like a Front Page to a 404 Page. 

> Select the **Page** option, to create a new page template.

The page template will be created, and you'll be taken to the editor to add blocks to the template.

Because a page in WordPress is merely a custom post type, you can use the Post Title, Post Featured Image, and Post Content blocks to render the title, featured image, and content of a page in the template.

> 1. Add a Post Title block to the page template.
> 2. Add a Post Featured Image block to the page template.
> 3. Add a Post Content block to the page template.

Your final page template should look something like this:

![Image of the page template with the post title, post featured image, and post content blocks](/images/module-02/page-template.png)

Now switch to the Code editor view, to see the block markup that makes up this page template

```html
<!-- wp:post-title /-->

<!-- wp:post-featured-image /-->

<!-- wp:post-content /-->
```

Finally, remember to exit the Code editor view, before saving the template.

> Save this template now, so it's included when we export it later!

### Further Reading

You can read more about the [block theme templates](https://developer.wordpress.org/themes/block-themes/templates-and-template-parts/)in the Theme Handbook.

Now that we've covered theme templates, let's take a look at template parts.