# Disabling Theme Settings in theme.json

The `theme.json` file is a powerful tool that allows theme authors to control much of the block-editing experience.  Its primary roles are to allow developers to opt into specific design-related settings and create custom styles.

In this lesson, you will learn how to curate that experience by enabling or disabling specific design settings.

## Disable/Enable Specific Settings

Your theme should have a `theme.json` file that is structured similar to the following:

```json
{
	"$schema": "https://schemas.wp.org/trunk/theme.json",
	"version": 2,
	"settings": {},
	"styles": {}
}
```

This lesson specifically focuses on items nested under the `settings` key.  Some of the top-level settings you can configure include the following:

- `border`
- `color`
- `layout`
- `spacing`
- `typography`

This lesson will not cover every conceivable setting that you can enable/disable.  You can find the full and most current list via the [settings section](https://developer.wordpress.org/block-editor/reference-guides/theme-json-reference/theme-json-living/#settings) in the `theme.json` living reference.

Each setting controls a specific aspect of the editing experience.  For this lesson, let's take a look at `border` as an example.  It allows you to control whether users can set a block's border color, radius, style, or width.

The `border` setting is an object with four keys that you can set.  The default object looks like the following:

```json
"border": {
	"color": false,
	"radius": false,
	"style": false,
	"width": false
},
```

If you are building a theme and don't want users to edit borders, you could simply do nothing in this case.  Each of the default values are already set to `false`.

However, if you wanted to enable one or more settings, you would need to set each to `true`.

Let's imagine that you are building a theme for a client and have carefully designed borders to use a specific style and radius.  However, you are comfortable with giving them control over the color and width.  

> **Do:** You only need to set the `color` and `width` keys to `true`, as shown in the following `theme.json` example:

```json
{
	"settings": {
		"border": {
			"color": true,
			"width": true
		}
	}
}
```

In the post or site editor, users should see the following border controls:

![WordPress post editor with a Group block. The border control is selected in the sidebar with a specific color and width selected.](/images/module-09/lesson-01/limited-border-settings.png)

You can also set up default settings but overrule them for specific blocks.  For example, perhaps you want to allow your theme users to edit all aspects of a block's border, except you don't want them to change the radius on the Group block.  

> **Do:** For this, you would need to set both `settings.border` and `settings.blocks[core/group].border`, as shown in the following code snippet:

```json
{
	"settings": {
                "border": {
                        "color": true,
                        "radius": true,
                        "style": true,
                        "width": true
                },
		"blocks": {
			"core/group": {
				"border": {
					"radius": false
				}
			}
		}
	}
}
```

You can mix and match these however you want, providing more or less control at the global level or down to the individual block.

Each of the available settings provides this level of granularity over what design tools are shown to the end-user.  Alone, they give you precise oversight of the controls available.  When configuring multiple settings, you can create a holistic design experience that is specific to your vision.

## Appearance Tools

One of the settings that developers can opt into is `appearanceTools`.  This allows you to quickly set up several appearance-related settings. However, it can be a double-edged sword, which you'll learn about in this section.

> **Do:** To enable the setting, set it to `true` in your `theme.json` (the default is `false`):

```json
{
	"settings": {
		"appearanceTools": true
	}
}
```

Enabling this setting automatically opts the theme into most of the design-related tools.  Essentially, it is shorthand for the following:

```json
{
	"settings": {
                "border": {
                        "color": true,
                        "radius": true,
                        "style": true,
                        "width": true
                },
		"color": {
			"link": true
		},
		"spacing": {
                        "blockGap": true,
                        "margin": true,
                        "padding": true
		},
		"typography": {
			"lineHeight": true
		}
	}
}
```

Enabling support will make the design tools appear in the site editor or on individual blocks (for those that support each tool), as shown in the following screenshot:

![WordPress page editor with a Group block in the content and the block inspector in the sidebar, which shows color, typography, dimensions, and border design tools.](/images/module-09/lesson-01/appearance-tools.png)

For theme authors who always want to support all or most of those appearance tools, this is an easy way to cut back on code in `theme.json`.

It is also possible to set `appearanceTools` to `true` and then opt out of individual settings if you prefer to disable them.

> **Warning** Opting into `appearanceTools` could also automatically opt the theme into future appearance tools not listed.  Currently, it's limited to border, color, spacing, and typography.  However, WordPress may add box-shadow or other design tools down the road.

Because of the aforementioned warning, developers who want complete control over the design settings their themes offer should not enable `appearanceTools`.  Potential future tools are unknowns and could spoil a carefully-crafted system, particularly in agency and freelancing work for clients.
