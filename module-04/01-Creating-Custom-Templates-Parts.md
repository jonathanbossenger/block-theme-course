# Creating Custom Templates and Template Parts

In the module on Building Your Theme Structure in the Editor, you learned about the WordPress template hierarchy, the primary templates every block theme needs, and how to create those primary templates in the Site Editor.

During that process, you selected the specific template to be created from the list of available templates in the **Add new template** interface.

![Adding a new template](https://learn.wordpress.org/files/2022/10/add-new-template.png)

For most themes, this list of templates is sufficient, but what if you wanted to create a custom template that has a specific function? 

If you look at the Twenty Twenty-Three templates, you'll see a couple of custom templates, including a blank page template with only the post content and an alternative blog page template without featured images. These templates were created, so that users can choose to apply them to specific pages or posts respectively. 

## Creating custom templates

Since WordPress 6.1, we've had a new option in the list of new templates to add, the **Custom template** option. As the name suggests, this can be used to create a custom template that can be applied to any post or page.

![Adding a new template](https://learn.wordpress.org/files/2022/10/add-new-custom-template.png)

Using this option, you can now create and edit your alternative page and post templates.

> **Do** Create the alternative page template
> 1. Navigate to the list of templates in the Site Editor.
> 2. Click the **Add New Template** plus sign icon.
> 3. Select **Custom template** from the list of available templates.
> 4. Give the template a name - "Page (Alternative)".
> 5. Choose the available pattern for pages.

![Adding a new template](https://learn.wordpress.org/files/2022/10/add-new-custom-page-template.png)

You will note that it auto-populates your new template with some content. In this case, it uses the content from the **Page** template.

![Adding a new template](https://learn.wordpress.org/files/2022/10/added-new-custom-page-template.png).

You can now edit the alternative page template in the Site Editor, in this case, by removing the featured image, and saving the template

> **Do**  Edit the alternative page template
> 1. Edit the alternative page template by removing the **Post Featured Image** block.
> 2. Save the template.

> **Note** The Twenty Twenty-Three theme has a Blog (Alternative) page for displaying a feed of posts, however, there's no alternative single post template. To apply a custom template to a single post you can create a new custom template and build it from scratch. To start, after clicking the **Add New Template** plus sign icon to create a new template, select the **Single item: Post** option.

**Option to add new screenshot here: single-item-post.png**

## Creating custom template parts

Just as you can create custom templates to be used for specific purposes, you can create custom template parts. Headers and footers are commonly reusable template parts, but you don't have to limit yourself to these two options.

For example, things like the post meta group you created for the single template in the previous lesson on Building the Primary Templates in the Editor, are perfect to use for creating a template part. You can then reuse the template part in any post-related templates you create.

Depending on how you're developing your theme, you can either take blocks, or collections of blocks, from an existing template and create a template part from them, or you can create a template part from scratch.

Either way, the main difference between creating a header or footer template part, or a custom template part, is that you choose the **General** area when creating a custom template part.

## Creating a custom template part from a template

To create a template part from an existing template, edit a template, select the block or group of blocks you want to turn into a part, and use the *Create template part** option.

> **Do** Create a new custom template part for post meta from the single post template
> 1. Edit the Single Template.
> 2. In the List view, select the post meta group.
> 3. Click on the Group options and select **Create template part**.
> 4. Give the template part a name - "Post Meta".

![Adding a new template part](https://learn.wordpress.org/files/2022/10/create-template-part.gif)

The template part will be created, and it will be added to the template in the editor. If you view your list of template parts, you'll see the new template part in the list.

![Template part list](https://learn.wordpress.org/files/2022/10/template-part-list.png)

