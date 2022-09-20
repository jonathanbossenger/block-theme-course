# Exporting Your Block Theme

Once you have created your basic theme structure, enabled or disabled settings and applied styles in your theme.json, and created your templates and template parts, your final step is going to be exporting all of this from your WordPress install into an installable theme zip file. After all, the theme you've just designed is not meant to stay in this WordPress installation, it might be meant for a client site, or you're planning to release it on the WordPress.org theme repository. 

This lesson will walk you through the steps to export your theme.

## Manually Exporting Your Theme

The process to manually export your theme involves a few steps, which you must follow for each template and template part in your theme:

1. Navigate to the template or template part in the Site Editor.
2. Click the "More Options" button in the top right corner of the editor and select the Code Editor option to view the block markup code.
3. Copy the block markup code for the template or template part and paste it into the relevant file in your theme directory.
4. Save the file, and then repeat these steps for each template and template part in your theme.

This process is a bit tedious, but it's good to review how to do it, because it helps to understand the structure of the block theme, especially as it pertains to directory structure.

### Block Theme Template structure

In classic themes, template files are located in the root of the theme directory whereas in block themes, template files are located in a directory called `templates`. You already created this directory when you created the emtpy index.html file in an earlier lesson.

Template parts on the other hand are located in a directory called `parts`. 

Both template files and template parts are html files that contain a mix of HTML and block markup. These files follow the same naming convention as the Template Hierarchy, namely:

1. the file name is all lower case and matches a template hierarchy slug (eg index.html, single.html, archive.html, etc)
2. the slug uses hyphens to separate words (eg single-post.html, archive-post.html, etc)

<div class="callout callout-tutorial">
    Now would be a good idea to switch to your code editor and create the `parts` directory in your theme's directory
</div>

### Manually exporting templates

To manually export the index template, navigate to the template and switch to the Code editor view, then copy the block markup code into the index.html file in the templates directory.

<div class="callout callout-tutorial">
    1. Copy the block markup from the Code editor View
    2. Navigate to the `templates` directory of your theme, and open the index.html file
    3. Paste the block markup into the index.html file, and save the file.
</div>

If you refresh the Site editor, you will see the changes you made to the index.html template file. (to be confirmed)

If you wanted to follow the process for the page template, you'd first create the page.html template file in the `templates` directory, and copy the code from the page template in the editor.

<div class="callout">
    Create the page.html template file now, and copy the block markup from the page template in the Site editor.
</div>

## Manually exporting template parts

As you did with templates, you're going to want to export your template parts to the relevant template parts file, in this case the `header.html` template part and the `footer.html` template part. 

<div class="callout callout-tutorial">
    Repeat the process of editing, copying and saving the header and footer template parts to their respective files
</div>

You should now have 4 template files on your block theme:

1. templates/index.html
2. templates/page.html
3. parts/header.html
4. parts/footer.html

[Image of the newly created parts directory]

## Using the Site Editors Export Tool

While manually exporting templates and template parts helps with understanding how a block theme is built, it's not the most suitable solution. Not only is it tedious, but if you've made changes to the Global Styles, you have no way of also exporting those changes. 

Fortunately The Site Editor has an export tool that will export all of your block theme code into an installable theme zip that you can then install on another WordPress site. You can access the export tool from the Site Editor's More Options menu, by clicking on the three dots.

Using this export tool will export all of your templates, template parts, and Global Styles into a zip file that you can then install on another WordPress site.

## Using the Create Block Theme Plugin

