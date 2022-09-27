# Creating a Primary Templates

As discussed in the [Create a Block Theme (Low-Code) course](https://learn.wordpress.org/create-a-block-theme/), the primary WordPress templates are:
- index
- singular
- archive
- single
- page
- home
- 404
- search

These are the minimum templates that a WordPress theme needs to have in order to cover all content use cases. 

In the recap of templates lesson, you created the index and page templates. Now, you can create the rest of the primary templates in the editor. A good place to start would be the single post template, as it would be used for displaying a single post, and also as a fallback for any custom post type.

## Template Content

As mentioned in the first lesson of this module, you will be building the templates, based on the Twenty Twenty Three theme.

![Twenty Twenty Three Designs](/images/module-02/lesson-02/twenty-twenty-three-design.png)

If you look at the Base Theme, and zoom into the Single Post layout, you can see the following elements:
1. It uses the header and footer template parts.
2. It contains the featured image, at 1000px wide
3. This is followed by the post title, also at 1000px wide
4. Then the post content, which is 650px wide
5. Next is the post meta, which is 1000px wide
6. Finally, the comments section, which is 650px wide

Take a look at the theme.json code that you added in the last lesson, specifically the `layout` setting. The `contentSize` and `wideSize` layout settings match the sizes in the design. You would have set these values from the designs you were given when you created the global settings and styles in the previous step.

## Create a Primary Template

Creating the single template follows the same process you followed when creating the page template.

> 1. Navigate to the list of templates in the editor
> 2. Click the "Add New" button
> 3. Select the "Single" template from the list

The editor will create the single template, and populate it with a copy of the content from your index template. You can then edit the template to add/remove the content you want to display for a single post. 

> **Do:** Delete all the content from the new single post template, except for the header and footer

Based on the layout of the Single Post template, you can start by adding the following layout blocks:

> **Do:** Create the Single Post template layout
> 1. Add the header Template Part
> 2. Add a **Group** block to serve as the content container
>    1. Add a Group block inside the content container Group block. We'll call this the headline Group block, and it will contain the post title and featured image
>    2. Add a Spacer block after the headline Group block
>    3. Add the Post Content block after the Spacer
>    4. Add another Spacer after the Post Content block
>    5. Add another Group block after the second Spacer block. We'll call this the postmeta Group block. It will contain the post meta data and the comments section
> 3. Finally, add the footer Template Part

- Archive
- Front Page - the home template
- 404
- Search

Once you've created your templates in the editor, you can export your theme templates using one of the export options discussed in a previous lesson.

> Pro Tip. The Overwrite option of the Create Block Theme plugin is very useful here. It allows you to save the changes you've made in the editor to the correct files in the current theme, and clears out any changes stored in the database. This is useful if you want to store your theme changes to a revision control system, like Git.

Which ever option you used to export your template content, your theme directory will start coming together as you build the various templates.

![Theme Structure](/images/module-02/lesson-02/block-theme-primary-templates.png)

