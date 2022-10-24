# Disabling Theme Settings in theme.json

!! Write and actual intro !!

## Disable/enable specific settings in the Site editor

This lesson will not cover every conceivable setting that you can enable/disable.  You can find the full and most current list via the [settings section](https://developer.wordpress.org/block-editor/reference-guides/theme-json-reference/theme-json-living/#settings) in the `theme.json` living reference.

Top-level settings:

- `useRootPaddingAwareAlignments`
- `border`
- `color`
- `layout`
- `spacing`
- `typography`

## Appearance Tools

```json
{
	"settings": {
		"appearanceTools": true
	}
}
```

Opting into this setting automatically opts the theme into several appearance-related settings and sub-settings.  Essentially, it is shorthand for:

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

Either of the following will make the design tools appear in the site editor or on individual blocks (for those that support each tool), as shown in the following screenshot:

-- INSERT SCREENSHOT --

It is possible to set `appearanceTools` to `true` and then opt out of individual settings if you prefer to disable them.

For theme authors who always want to support all or most of those appearance tools, this is an easy way to cut back on code in `theme.json`.

> **Warning**\
> Opting into `appearanceTools` could also automatically opt the theme into future appearance tools.  Currently, it's limited to border, color, spacing, and typography.  However, WordPress may add box-shadow or other design tools down the road.

Because of the aforementioned warning, developers who want complete control over the design tools their themes offer should not enable `appearanceTools`.  Potential future tools are unknowns and could spoil a carefully-crafted system, particularly in agency and freelancer work.
