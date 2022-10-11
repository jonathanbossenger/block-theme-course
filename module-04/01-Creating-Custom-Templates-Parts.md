# Creating Custom Templates and Template Parts

In the module on Building Your Site Structure in the Editor, you learned about the WordPress template hierarchy, the primary templates every block theme needs, and how to create those primary templates in the Site Editor.

During that process, you selected the specific template to be created from the list of available templates in the **Add new template** interface.

![Adding a new template](/images/module-04/lesson-01/add-new-template.png)

For most themes, this list of templates is sufficient, but what if you wanted to create a custom template, either one higher up in the hierarchy, or one that has a specific function. 

For example, let's say you want to create a custom post template in your theme, to be used when a featured author is writing a post. 

The requirements are:
1. The post title should be at the top of the page, and centered to the page
2. The post author and post date should display below the title, and center justified
3. The author's bio should be displayed below author name and date, center justified
4. The featured image should follow the bio
5. The post content should follow the featured image

## Creating custom templates

The WordPress 6.1 release included a new template option in the list of new templates to add, the Custom template option. As the name suggests, this can be used to create a custom template, either a specific one in the template hierarchy, or a template that can be applied to any post or page.

As the Featured Author template will only be applied on a per-post basis, it doesn't need to be created to match any specific template in the hierarchy. For now you can create the template, and then apply it to a specific post.

> **Do** Create the Featured Author Post template
> 1. Navigate to the list of templates in the editor
> 2. Click the "Add New" button
> 3. Select "Custom template" from the list of available templates
> 4. Give the template a name - "Featured Author Post"

As before, when you create the new template, it auto populates it with the same content from the index template, and redirects you to the template editor.

> **Do** Edit the new template to match the theme requirements
> 1. 

> **Do** Apply the template to a specific post
> 1.

### Export the custom template

Either manually or using Create Block Theme

### Register the template in theme.json

```json
"customTemplates": [
		{
			"name": "featured-author-template",
			"title": "Featured Author Template",
			"postTypes": [
				"post"
			]
		}
	],
```

## Creating specific templates

Create a template for a specific post by slug

https://developer.wordpress.org/themes/basics/template-hierarchy/#single-post

> **Do** Create a new custom post template for the post by slug
> 1. Create the template
> 2. Edit the template
> 3. Export the template, and rename it to match the required template name
> 4. Register the template in theme.json

## Creating custom template parts

> **Do** Create a new custom template part for comments
> 

Export
Register in theme.json

```json
	"templateParts": [
		{
			"area": "general",
			"name": "post-comments",
			"title": "Post Comments Part"
		},
	],
```

While we are here, let's register the header and footer as well

```json
		{
			"area": "header",
			"name": "header",
			"title": "Header Part"
		}, 
		{
			"area": "footer",
			"name": "footer",
			"title": "Footer Part"
		}
```

> **Do** Add the template parts to a template
> 1. In the Site Editor
> 2. Manually
