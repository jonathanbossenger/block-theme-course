# Registering Custom Font Families via theme.json

WordPress allows themes to define font families via their `theme.json` file.  This can include standard, web-safe fonts (e.g., Times New Roman, system-ui, sans-serif, etc.) or bundled web fonts via a font-face definition.

In the previous lesson, you downloaded and stored the Open Sans font in your theme folder.  Now, let's register it.

Themes can register their font families via the `settings.typography.fontFamilies` array.  And, each family can register one or more objects via the `fontFace` key.  

Let's take a look at what a `fontFace` array should look like for Open Sans:

```json
"fontFace": [
	{
		"fontFamily": "Open Sans",
		"fontWeight": "300 800",
		"fontStyle": "normal",
		"fontStretch": "normal",
		"src": [ "file:./assets/fonts/OpenSans-VariableFont_wdth,wght.woff2" ]
	},
	{
		"fontFamily": "Open Sans",
		"fontWeight": "300 800",
		"fontStyle": "italic",
		"fontStretch": "normal",
		"src": [ "file:./assets/fonts/OpenSans-Italic-VariableFont_wdth,wght.woff2" ]
	}
]
```

Note that we included both of the font files and set the values based on the style and available weights of each.

Those familiar with the `@font-face` [CSS at-rule](https://developer.mozilla.org/en-US/docs/Web/CSS/@font-face) should see the similarities between it and this JSON-based counterpart.  The work nearly the same.  `fontFamily` maps to `font-family` in CSS, `fontWeight` maps to `font-weight`, and so on.

However, one of the differences here is the format of the `src` file:

```json
"src": [ "file:./assets/fonts/OpenSans-VariableFont_wdth,wght.woff2" ]
```

In particular, the `file:` bit at the beginning.  Essentially, that lets WordPress know to look for a file in the theme, and the actual path should be relative to the folder where the `theme.json` file is located.

When registering a `fontFace`, it must be paired with a font family object in the `theme.json`.  This object should have a `name`, `slug`, and `fontFamily` (i.e., font stack) registered.

Here is what an entire font family object looks like:

```json
{
	"name": "Open Sans",
	"slug": "open-sans",
	"fontFamily": "\"Open Sans\", sans-serif",
	"fontFace": [
		{
			"fontFamily": "Open Sans",
			"fontWeight": "300 800",
			"fontStyle": "normal",
			"fontStretch": "normal",
			"src": [ "file:./assets/fonts/OpenSans-VariableFont_wdth,wght.woff2" ]
		},
		{
			"fontFamily": "Open Sans",
			"fontWeight": "300 800",
			"fontStyle": "italic",
			"fontStretch": "normal",
			"src": [ "file:./assets/fonts/OpenSans-Italic-VariableFont_wdth,wght.woff2" ]
		}
	]
}
```

Theme authors can include multiple family objects via the `settings.typography.fontFamilies` array.  For the purposes of this lesson, we will only register the Open Sans font.

Now, let's take what we've learned and put it into practice.  Open your `theme.json` file and put your Open Sans font code inside the `fontFamilies` array:

```json
{
	"version": 2,
	"settings": {
		"typography": {
			"fontFamilies": [
				{
					"fontFamily": "\"Open Sans\", sans-serif",
					"name": "Open Sans",
					"slug": "open-sans",
					"fontFace": [
						{
							"fontFamily": "Open Sans",
							"fontWeight": "300 800",
							"fontStyle": "normal",
							"fontStretch": "normal",
							"src": [ "file:./assets/fonts/OpenSans-VariableFont_wdth,wght.woff2" ]
						},
						{
							"fontFamily": "Open Sans",
							"fontWeight": "300 800",
							"fontStyle": "italic",
							"fontStretch": "normal",
							"src": [ "file:./assets/fonts/OpenSans-Italic-VariableFont_wdth,wght.woff2" ]
						}
					]
				}
			]
		}
	}
}
```

At this point, Open Sans is now registered as a font with WordPress via your theme.  The next lesson will walk you through applying it via the Styles interface in the site editor.
