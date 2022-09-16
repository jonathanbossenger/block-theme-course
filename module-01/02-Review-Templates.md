# Block Theme Templates

[Short video covering this lesson]

The core files that make up a WordPress theme are templates. [Templates](https://developer.wordpress.org/themes/basics/template-files/) are the files that WordPress uses to render the content of a post or page. 

In a classic theme templates are PHP files that contain HTML and PHP code. In a block theme, templates are HTML files that contain HTML and block markup. Both classic and block theme templates follow the WordPress [Template Hierarchy](https://developer.wordpress.org/themes/basics/template-hierarchy/).

The Template Hierarchy is the logic WordPress uses to decide which theme template file to use when rendering content. By creating template files that follow the Template Hierarchy naming convention WordPress can automatically determine which template file to use for a given piece of content.

For example, to render the content for a single post, you can create any of the [single post template files](https://developer.wordpress.org/themes/basics/template-hierarchy/#single-post), and WordPress will use the first one it finds in the theme directory. 

## Template File Location

In classic themes, template files are located in the root of the theme directory whereas in block themes, template files are located in a directory called `templates`. This makes a block theme directory much cleaner and easier to navigate, as there are no other files in the `templates` directory than theme templates.

## Creating New Templates

One of the main advantages of block themes over classic themes, is that you can create new theme templates from the Site Editor. Once created, you can either save the template for the current site, which stores it in the database, or export the template code into a file in the `templatess` directory of your theme. 

In the Create a Block Theme (Low-Code) course, you created a couple of block theme templates. 

[Image of one of the templates created in the previous course]

Then you exported your theme, which exported the code for the templates into the theme's `templates` directory.

[Image of the style guide template in the Theme's templates directory]

Now, create a new template by navigating to the Editor. Toggle the Editor navigation menu, and select Templates.

[Image of the list of templates in the Editor created in the previous course]

Click on the Add New button to create a new template. The Editor will give you the option of creating a new template based on the template type, ranging from things like a Front Page to a 404 Page. For this lesson, select the Page option, to create a new Page template.

[Image of the list of templates in the Editor created in the previous course]

In the Create a Block Theme (Low-Code) course you also created a header and footer template, so start by adding the header template. 

You can do this in two ways:

1. Click on the Block Inserter Button, and selecting the Header block from the list.

[Image of the Block Inserter Button]

2. Type /header in the editor, and select the Header block.

[Image using the /header shortcut to insert the Header block]

Either way, once your Header block is added, you can Choose your header template part to insert it into the page template.

[Image of the Header block selection]

Next, add the Post Title and Post Content blocks to the template. 

<callout>Because a page in WordPress is merely a custom post type, you can use the Post Title and Post Content blocks to render the title and content of a page.</callout>

Finally, add the footer template part to the page template, in the same way you added the header.

Your final page should look something like this.

[Image of the page template with the header, post title, post content and footer template parts]

Don't save this page at this point, because you're going to want to export this code to a template file.

## Exporting Templates

Now that you have created a new template, you can export it to a file in the theme's `templates` directory. Click on the Editor options and switch to the Code editor view. You'll see the block code in the editor.

[Image of the page template in the Code editor view]

You can now copy this code, create a new template file called page.html in the theme's `templates` directory, and paste the code into the file.

Once you've done that, refresh the Site Editor, either by using your browser's refresh button, or by navigating back to the dashboard, and then back to the Site Editor.

If you navigate to your list of templates, you'll now see a Page template in the list. 