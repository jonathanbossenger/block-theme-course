# Creating a Primary Template

In the first two lessons of Module 1, you created the `index.html` and `page.html` templates. Now, you can create the rest of the primary templates in the Site Editor. A good place to start would be the `single.html` template, as it would be used for displaying a single post, and also as a fallback for any custom post type.

## Template Content

As mentioned in the first lesson of this module, you will be building the templates, based on the Twenty Twenty-Three theme.

![Twenty Twenty-Three Designs](https://learn.wordpress.org/files/2022/10/twenty-twenty-three-design.png)

## Create a Primary Template

Creating the single template follows the same process you followed when creating the page template.

> 1. Navigate to the list of templates in the Site Editor
> 2. Click the **Add New Template** plus sign icon
> 3. Select the **Single Posts** template from the list
> 4. Choose the pattern from the Index template

The Site Editor will create the `single.html` template, and populate it with a copy of the content from your `index.html` template. You can then edit the template to add/remove the content you want to display for a single post. 

> **Do:** Delete all the content from the new `single.html` template, except for the header and footer.

Based on the layout of the Single Posts template, you can start by adding the following layout blocks:

> **Do:** Create the Single Posts template layout
> 1. Add a **Group** block to serve as the content container
> 2. Add a **Group** block inside the content container **Group** block. We'll call this the headline Group block, and it will contain the post title and featured image
> 3. Add a **Spacer** block after the headline **Group** block
> 4. Add the **Post Content** block after the **Spacer** block
> 5. Add another **Spacer** block after the **Post Content** block
> 6. Add another **Group** block after the second **Spacer** block. We'll call this the postmeta Group block. It will contain the post meta data and the comments section

> **Note:** It's a useful to first use Group and Spacer blocks to create the layout of a template, and then fill in the details. 

Now that you have the template layout in place, you can fill in the headline Group block with the post title and featured image.

> **Do:** Add the featured image, and set the alignments
> 1. Add the **Post Featured Image** block to the headline **Group** block
> 2. Add the **Title** block to the headline **Group** block
> 3. Set the alignment of headline **Group** block, the **Post Featured Image** block, and the **Title** block to **Wide width**

At the same time, you can set the Spacer block height to decrease the space between the headline and the post content.

> **Do:** Set the **Spacer** block height to 30px

Now, add the relevant blocks to the postmeta Group block.

> **Do:** Add the post meta data and the comments
> 1. Add a **Row** block to the postmeta **Group** block
> 2. Add the **Post Date**, **Post Author**, **Categories**, and **Tags** blocks to the **Row** block
> 3. Add a **Spacer** block after the **Row** block, and set it's height to 30px
> 4. Add a **Separator** block after the **Row** block
> 5. Add the **Comments** block after the **Separator** block

> **Tip:** Notice how when you add blocks to a Group block, they appear one below the other, but when you add blocks to a Row block, they appear next to each other.

Now you can tweak your `single.html` template to your liking. You can add/remove blocks, change the alignments, and so on. For now, save the template to make sure it's not lost.

You should be able to create the rest of your theme's primary templates. 

If you need inspiration, take a look at the [Block course theme repository](https://github.com/WordPress/block-course-theme), and see how the other templates were created.

- [404.html](https://github.com/WordPress/block-course-theme/blob/trunk/templates/404.html)
- [archive.html](https://github.com/WordPress/block-course-theme/blob/trunk/templates/archive.html)
- [blank.html](https://github.com/WordPress/block-course-theme/blob/trunk/templates/blank.html)
- [home.html](https://github.com/WordPress/block-course-theme/blob/trunk/templates/home.html)
- [index.html](https://github.com/WordPress/block-course-theme/blob/trunk/templates/index.html)
- [page.html](https://github.com/WordPress/block-course-theme/blob/trunk/templates/page.html)
- [search.html](https://github.com/WordPress/block-course-theme/blob/trunk/templates/search.html)
- [single.html](https://github.com/WordPress/block-course-theme/blob/trunk/templates/single.html)

Once you've created your templates in the Site Editor, you can export your theme templates using one of the export options discussed in a previous lesson.

> **Tip:** The **Overwrite** option of the Create Block Theme plugin is very useful here. It allows you to save the changes you've made in the editor to the correct files in the current theme, and clears out any changes stored in the database. This is useful if you want to store your theme changes to a revision control system, like Git.

Whichever option you used to export your template content, your theme directory will start coming together as you build the various templates.

![Theme Structure](https://learn.wordpress.org/files/2022/10/block-theme-primary-templates.png)

