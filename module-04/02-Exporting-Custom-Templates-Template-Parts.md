# Exporting Custom Templates and Template Parts

The big difference between the Primary (and Secondary) Templates and the Header and Footer template parts, and any custom templates or template parts you create, is how you export the code to theme files. 

The main reason for this is that custom templates and template parts do not have specific, predefined names within the Template Hierarchy system. 

For this reason, it's not possible to automatically export the code to a file name you specifiy, as it might be with a page, post, or single template, or a header or footer template part.

Instead, you might choose to manually export the code to a file to give it a specific name, and then register your custom templates and template parts in the theme.json file.

## Exporting Custom Templates

To start, export the alternative page template to a file. This process will follow the same process as described in the Manually exporting templates section of the Exporting theme files lesson from Module 01.

To manually export the alternative page template, navigate to the template and switch to the Code Editor view, then copy the block markup code into a file in the `templates` directory. The file name is arbitrary, but it should be descriptive of the template. For this example, call the file `page-alternative.html`.

> **Do:**
> 2. Create the `page-alternative.html` file in the `templates` directory
> 3. Navigate to the template and switch to the Code Editor view
> 4. Copy the block markup from the Code Editor View
> 5. Navigate to the `templates` directory of your theme, and open the `page-alternative.html` file in a text editor
> 6. Paste the block markup into the `page-alternative.html` file, and save the file.

## Exporting Custom Templates using the Site Editor export tool

If you choose to export your theme using the Export tool in the Site Editor, the custom template will be included in the exported theme files. 

The export will create the file in the templates' directory, with the following filename structure, where {template-slug} is a "slugified" version of the template name you specified when you create the template:

```
wp-custom-template-{template-slug}.html
```

> **Note:** the term slugified means that the template name is converted to lowercase, any non-alphabetical characters are removed, and any spaces are replaced with hyphens.

So if you create a template called `Alternative Page`, the file will be named `wp-custom-template-alternative-page.html`.

You can then rename the file to something more descriptive, such as `page-alternative.html`.

## Exporting Custom Templates using Create Block Theme

If you're using Create Block Theme, you can export custom templates using the `Overwrite New Block Theme` option. 

This option will create the file in the templates directory, using the same "slugified" version of the template name as the file name:

```
wp-custom-template-{template-slug}.html
```

As when using the Export tool, you then need to rename the file.

## Registering Custom Templates

Whether you export manually, use the Export tool, or use Create Block Theme, your final step is to register the custom template in the `theme.json` file. To do so, you add a new top level item called `customTemplates` to the file, and then add an object for each custom template.

```json
"customTemplates": [
		{
			
		}
	],
```

> **Note:** Note the use of the square brackets and the curly brackets here. The square brackets indicates that this is json array, and the curly brackets indicate that this is a json object. You can have multiple objects in the array, one for each custom template.

Then you can register your custom template, giving it a name, a list of postTypes, and a title:

```json 
"customTemplates": [
		{
			"name": "page-alternative",
			"postTypes": [
				"page"
			],
			"title": "Page Alternative"
		}
	],
```

> **Note:** The name of the custom template is the same as the file name, minus the `.html` extension. The postTypes array is the list of posts types that this template can be applied to. Because this is a page template, you only need to specify the `page` post type. The title is the name of the template as it will appear in the editor.

## A little housekeeping

If you switch back to the Site Editor, and refresh the Templates list, you'll see there are now two Page Alternative templates listed. 

![Duplicate Templates](https://learn.wordpress.org/files/2022/10/updated-custom-templates-list.png)

One is marked as added by your user, and the other as added by the theme. The one added by the user was created soley in the editor, and is therefore only stored in the database. The other is the file you just created and registered. You can therefore delete the one added by the user.

To practice this process, export the post alternative template you created in the previous lesson. Follow the same steps as you did for the alternative page

1. Export the template to the relevant template file
2. Register the template in theme.json
4. Delete the template added by the user

Remember to add the new custom template to the `customTemplates` array in the theme.json file, using a comma between each custom template object. Remember to also set the correct post type for the alternative post template

```json 
"customTemplates": [
		{
			"name": "page-alternative",
			"postTypes": [
				"page"
			],
			"title": "Page Alternative"
		}, 
		{
			"name": "post-alternative",
			"postTypes": [
				"post"
			],
			"title": "Post Alternative"
		},
	],
```

## Exporting Custom Template Parts

The general process to export custom template parts is the same as for templates, with the only really difference being how they are registered in `theme.json`.

Instead of using the `customTemplates` objects in `theme.json`, you use the `templateParts` object. This object has a similar structure to the `customTemplates` object, but instead of `postTypes`, you specify a template part `area` of "general".

```json
"templateParts": [
    {
        "area": "general",
        "name": "post-meta",
        "title": "Post Meta"
    },
],
```