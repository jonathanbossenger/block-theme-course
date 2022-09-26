# Exporting Your Block Theme

[Supplemental Video](https://videopress.com/v/ktmuF4cT)

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

In classic themes, template files are located in the root of the theme directory whereas in block themes, template files are located in a directory called `templates`. You already created this directory when you created the empty index.html file in an earlier lesson.

Template parts on the other hand are located in a directory called `parts`. 

Both template files and template parts are html files that contain a mix of HTML and block markup. These files follow the same naming convention as the Template Hierarchy, namely:

1. the file name is all lower case and matches a template hierarchy slug (eg index.html, single.html, archive.html, etc)
2. the slug uses hyphens to separate words (eg single-post.html, archive-post.html, etc)

> **Do:** Now would be a good idea to and create the `parts` directory in your theme's directory

![Create the parts directory](/images/module-01/lesson-04/parts-directory.png)

### Manually exporting templates

To manually export the index template, navigate to the template and switch to the Code editor view, then copy the block markup code into the `index.html` file in the `templates` directory.

> 1. Copy the block markup from the Code editor View
> 2. Navigate to the `templates` directory of your theme, and open the `index.html` file in a text editor
> 3. Paste the block markup into the `index.html` file, and save the file.

### Cleaning up site specific data

If you take a look at the code for the Query Loop block in your `index.html` template file, you'll notice that the `queryId` attribute is set to a value. This is the ID of the Query Loop block in your site, and it's not something you want to keep in your theme. So make sure to remove that attribute from the Query Loop block in your `index.html` file.

Before: 

```html
<!-- wp:query {"queryId":31,"query":{"perPage":3,"pages":0,"offset":0,"postType":"post","order":"desc","orderBy":"date","author":"","search":"","exclude":[],"sticky":"","inherit":true}} -->
```

After: 

```html
<!-- wp:query {"query":{"perPage":3,"pages":0,"offset":0,"postType":"post","order":"desc","orderBy":"date","author":"","search":"","exclude":[],"sticky":"","inherit":true}} -->
```

If you wanted to follow the process for the page template, you'd first create the `page.html` template file in the `templates` directory, and copy the code from the page template in the editor.

> **Do:** Create the page.html template file now, and copy the block markup from the page template in the Site editor.

## Manually exporting template parts

As you did with templates, you're going to want to export your template parts to the relevant template parts file, in this case the `header.html` template part and the `footer.html` template part. The main difference is that template parts are created in the `parts` directory.

>  **Do:** Repeat the process of editing, copying and saving the header and footer template parts to their respective files in the `parts` directory.

You should now have 4 theme files on your block theme:

1. templates/index.html
2. templates/page.html
3. parts/header.html
4. parts/footer.html

![Exported templates and template parts](/images/module-01/lesson-04/exported-templates-template-parts.png)

## Using the Site Editors Export Tool

While manually exporting templates and template parts helps with understanding how a block theme is built, it's not the most suitable solution. Not only is it tedious, but if you've made changes to the Global Styles, you have no way of also exporting those changes to the `theme.json` file. 

Fortunately The Site Editor has an export tool that will export all of your block theme code into an installable theme zip that you can then install on another WordPress site. You can access the export tool from the Site Editor's More Options menu, by clicking on the three dots.

![Accessing the export tool](/images/module-01/lesson-04/export-tool.gif)

Using this export tool will export all of your templates, template parts, and Global Styles into a zip file that you can then install on another WordPress site.

## Using the Create Block Theme Plugin

Another option for exporting your theme from the editor is the [Create Block Theme](https://wordpress.org/plugins/create-block-theme/) plugin. 

![Create Block Theme](/images/module-01/lesson-04/create-block-theme.png)

This plugin provides the same functionally as the editor's Export tool, but it also allows you to do the following:

1. Create a child theme of your current block theme, only exporting the changes made in the editor.
2. Clone your current block theme, and export all the changes made in the editor into a brand new block theme.
3. Overwrite your current block theme with the changes made in the editor.
4. Create a new "empty" block theme, ready for you to start editing.

If you prefer to keep a record of all the changes to your theme using revision control, like Git or SVN, the Create Block Theme and the Overwrite option is extremely valuable. You can make small changes to your theme in the Editor, Overwrite the changes to the theme files, and then commit those changes to your revision control system.