# Block Theme Templates

[Short video covering this lesson]

The core files that make up a WordPress theme are templates. [Templates](https://developer.wordpress.org/themes/basics/template-files/) are the files that WordPress uses to render the content of a post or page. 

In a classic theme templates are PHP files that contain HTML and PHP code. In a block theme, templates are HTML files that contain HTML and block markup. Both classic and block theme templates follow the WordPress [Template Hierarchy](https://developer.wordpress.org/themes/basics/template-hierarchy/).

The Template Hierarchy is the logic WordPress uses to decide which theme template file to use when rendering content. By creating template files that follow the Template Hierarchy naming convention WordPress can automatically determine which template file to use for a given piece of content.

For example, to render the content for a single post, you can create any of the [single post template files](https://developer.wordpress.org/themes/basics/template-hierarchy/#single-post), and WordPress will use the first one it finds in the theme directory. 

## Editing or Creating Templates

One of the main advantages of block themes over classic themes, is that you can edit existing templates or create new theme templates from the Site editor. 

<div class="callout">
    For a detailed breakdown of all the different parts of the Site editor, take a look at this [handy help document](https://wordpress.org/support/article/site-editor/).
</div>

You can then either save the template for the current site, which stores it in the database, or export the template code into the relevant file in the `templates` directory of your theme. 

### Adding Content to the index.html Template

In the last lesson, you create an empty `index.html` template file. Let's add some content to this template file.

Start by navigating to Appearance -> Editor. You'll be presented with a blank canvas, ready to add content to your index.html template.

[Image of the list of templates in the Editor created in the previous course]

As the index.html template is the default template that WordPress will load if it can't find a matching template file for the content being rendered, it's a good idea to add some content to this template. General best practice is to populate this template with a query loop, so that all posts on the site are displayed.

<div class="callout callout-tutorial">
    1. Add a heading block, and give the template a heading
    2. Add a query loop block, and select the "Standard" pattern for the query loop.
</div>

If you switch to the Code editor View, you'll be able to see the block markup for the heading and query loop blocks.

<div class="callout">
    Enable the Code Editor view by clicking the More Options three-dot menu and selecting Code editor.
</div>

```
<!-- wp:heading -->
<h2>A list of all my posts</h2>
<!-- /wp:heading -->

<!-- wp:query {"queryId":8,"query":{"perPage":3,"pages":0,"offset":0,"postType":"post","order":"desc","orderBy":"date","author":"","search":"","exclude":[],"sticky":"","inherit":false}} -->
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

If you save this template content, it will save the changes to the database. This means the template structure will only be available for this site. In lesson 4 of this module we'll review how to export the code to a template file. 

[Image of index template in the Site editor]

<div class="callout">
    Save this template now, we'll export it in a bit!
</div>

### Adding New Templates from the Site Editor

Besides adding block content to existing templates, you can also create brand new templates from the Site editor. 

To start, toggle to the Site editor navigation sidebar, and click on "Templates" in the editor navigation.

<div class="callout">
    If you don't see the Site editor navigation sidebar, click the WordPress logo in the top left corner of the editor, which is the  "Toggle Navigation" button.
</div>

You'll be presented with a list of the templates in this theme, and a button to add a new template.

<div class="callout callout-tutorial">
    Click on the Add New button to create a new template. 
</div>

The Editor will give you the option of creating a new template based on the template type, ranging from things like a Front Page to a 404 Page. 

<div class="callout callout-tutorial">
    Select the Page option, to create a new Page template.
</div>

[Image of the list of templates in the Editor created in the previous course]

Now you can add content to your page template.

<div class="callout callout-tutorial">
    Add the Post Title, Post Featured Image and Post Content blocks to the page template.
</div>

Because a page in WordPress is merely a custom post type, you can use the Post Title and Post Content blocks to render the title and content of a page.

Your final page template should look something like this:

[Image of the page template with the post title, post featured image, and post content blocks]

Now switch to the Code editor view, to see the block markup that makes up this page template

```html
<!-- wp:post-title /-->

<!-- wp:post-featured-image /-->

<!-- wp:post-content /-->
```

<div class="callout">
    Save this template now, so it's included when we export it later!
</div>

### Further Reading

You can read more about the [block theme templates](https://developer.wordpress.org/themes/block-themes/templates-and-template-parts/)in the Theme Handbook.

Now that we've covered theme templates, let's take a look at template parts.