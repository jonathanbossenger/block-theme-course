## Creating Variable Templates

Besides the primary and secondary templates, the WordPress Template Hierarchy supports templates for specific types of content types called variable templates. 

These templates are used in specific cases, for example, all posts by a specific author, or all posts in a specific category.

You can create variable templates using the Site Editor in the same way as described in the previous lesson, making sure that when you export the block markup to a template file, you create the filename to match the name that the template hierarchy requires.

For example, if you wanted to create a template for all posts by a specific author, you would create a template with the filename `author-{slug}.html` where `{slug}` is the nicename, or nickname, of the author.

Then, you can register the template in theme.json in the usual way:

```json
"customTemplates": [
		{
			"name": "author-johndoe",
			"title": "Author John Doe"
		}
	],
```

You don't need to specify the postTypes item, because this template will only be used when displaying the post archive by the specified author.