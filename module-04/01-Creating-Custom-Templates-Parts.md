# Creating Custom Templates and Template Parts

In the module on Building Your Site Structure in the Editor, you learned about the WordPress template hierarchy, the primary templates every block theme needs, and how to create those primary templates in the Site Editor.

During that process, you selected the specific template to be created from the list of available templates in the **Add new template** interface.

![Adding a new template](https://learn.wordpress.org/files/2022/10/add-new-template.png)

For most themes, this list of templates is sufficient, but what if you wanted to create a custom template that has a specific function. 

If you look at the Twenty Three designs, you'll see a couple of custom templates, including a page template without a featured image, and a post template without a featured image. These templates will need to be created, so that users can choose to apply them to specific pages or posts respectively. 

## Creating custom templates

The WordPress 6.1 release includes a new template option in the list of new templates to add, the **Custom template** option. As the name suggests, this can be used to create a custom template that can be applied to any post or page.

![Adding a new template](https://learn.wordpress.org/files/2022/10/add-new-custom-template.png)

Using this option, you can now create and edit your alternative page and post templates.

> **Do** Create the alternative page template
> 1. Navigate to the list of templates in the editor
> 2. Click the **Add New** button
> 3. Select **Custom template** from the list of available templates
> 4. Give the template a name - "Page (Alternative)"

![Adding a new template](https://learn.wordpress.org/files/2022/10/add-new-custom-page-template.png)

As before, when you create the new template, it autopopulates it with some content, in this case it uses the content from the **Page** template.

![Adding a new template](https://learn.wordpress.org/files/2022/10/added-new-custom-page-template.png)

You can now edit the alternative page template in the editor, in this case, by removing the featured image, and saving the template

> **Do** Create the alternative post template, using the same steps for the alternative page template.

## Creating custom template parts

Just as you can create custom templates to be used for specific purposes, you can create custom template parts. Headers and footers are commonly reusable template parts, but you don't have to limit yourself to these two options.

For example, things like post meta group you created for the single template in the previous module on Creating Primary Templates is perfect to create as a template part. You can then reuse the part in any post related templates you create.

Depending on how you're developing your theme, you can either take blocks, or collections of blocks, from an existing template and create a template part from them, or you can create a template part from scratch.

Either way, the main difference between creating a header or footer template part, or a custom template part, is that you choose the **General** area when creating a custom template part.

## Creating a custom template part from a template

To create a template part from an existing template, edit a template, select the block or group of blocks you want to turn into a part, and use the *Create template part** option.

> **Do** Create a new custom template part for post meta from the single post template
> 1. Edit the Single Template
> 2. In the List view, select the post meta group
> 3. Click on the Group options and select **Create template part**
> 4. Give the template part a name - "Post Meta"

![Adding a new template part](https://learn.wordpress.org/files/2022/10/create-template-part.gif)

The template part will be created, and it will be added to the template in the editor. If you view your list of template parts, you'll see the new template part in the list

![Template part list](https://learn.wordpress.org/files/2022/10/template-part-list.png)

