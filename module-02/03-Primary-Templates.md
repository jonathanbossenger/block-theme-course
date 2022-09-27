# Primary Templates

In the Block Theme Templates module, we briefly discussed the [WordPress Template Hierarchy](https://developer.wordpress.org/themes/basics/template-hierarchy/) and how it's used to determine which template file to use when rendering content. 

> The process of how the template hierarchy works, and how WordPress determines which template to render is beyond the scope of this course, and so we recommend reading the [Template Hierarchy](https://developer.wordpress.org/themes/basics/template-hierarchy/) documentation to learn more.

## Listing the Primary Templates

If you take a look at the template diagram shows which template files used based on the WordPress template hierarchy, you will notice that there are 8 **primary templates**. These are the templates that all themes, classic or block, should have to be considered a complete theme.

![Template Diagram](https://developer.wordpress.org/files/2014/10/Screenshot-2019-01-23-00.20.04.png)

The primary templates slugs are:
- index
- singular
- archive
- single
- page
- home
- 404
- search

In a classic theme, each of these template slugs relates to a physical file in the theme directory. For example, the `index.php` file is used to render the content for the index template.

## Template Hierarchy in Block Themes

In a block theme, the same template hierarchy is used. However, as you've already seen, instead of looking for a PHP file in the root of a theme directory, when WordPress is rendering content for a block theme, it knows to look for an HTML file in the `templates` directory.

## Creating the Primary Templates in the Editor

The Site editor allows you to create and edit the primary templates for a block theme. When you created the page template in a previous lesson, that was a primary template. This means you can also create the rest of the primary templates in the editor, and then either manually export them to the correct file, or use one of the automatic export methods we covered in the last lesson.

In the next lesson, you'll create one of primary templates for a block theme.
