# Converting the Style Guide to theme.json

The first step a developer usually takes is turning the style guide from the given designs into CSS. With the introduction of the theme.json file, this process is made a little easier. 

# Populating theme.json - Settings and Styles

## Creating a Global Setting

To create your first setting, let's apply the system wide theme font. Take a look at the Twenty Twenty Three style guide in the Figma file you copied earlier. 

The base font is either the default system font of the operating system, or the fallback is San Serif.

To implement this in the `theme.json` file, you first create a system wide Typography setting in the `settings` of your theme.json, which will generate a CSS variable when the theme is rendered. 

> **Do** Create the `typography` section in the theme.json "settings" and populate it with the relevant values. 

```json
{
  ...
  "settings": {
    "typography": {
      "fontFamilies": [
        {
          "fontFamily": "-apple-system,BlinkMacSystemFont,\"Segoe UI\",Roboto,Oxygen-Sans,Ubuntu,Cantarell,\"Helvetica Neue\",sans-serif",
          "name": "System Font",
          "slug": "system-font"
        }
      ]
    },
  ...  
}
```

> **Note** 
> - The `fontFamily` value is the CSS value of the font
> - The `name` value is the name of the font as it will appear in the Site editor
> - The `slug` value is used to create the CSS variable, using the following format `--wp--preset--font-family--{slug}`

This creates a CSS preset variable called `--wp--preset--font-family--system-font` that can be used in the theme's Global Styles. 

To apply this font setting to your theme, you can select this preset in the Global Styles interface in the Editor.

## Applying a Setting in the Global Styles Interface

Switch back to the Site editor, open the Global Styles interface, and apply the new font in the Typography section.

> **Do** 
> 1. Open the **Global Styles** interface.
> 2. Click **Typography**.
> 3. Click **Text**.
> 4. Select **System Font** from the **Font** dropdown.

![Applying a Global Font](/images/module-02/lesson-02/global-styles-fonts.gif)

Instantly you'll notice that the font in the template in the editor has been updated to the new font.

![System Font Applied](/images/module-02/lesson-02/system-font-applied.png)

Make sure to save your Custom Styles, to ensure they are applied to the theme.

## Applying a Setting in the theme.json File

If you prefer to manually add the setting to the `theme.json` file, you can do so by adding the following to the `styles` section.

> **Do** Update the `styles` section in the theme.json and apply the --wp--preset--font-family--system-font CSS variable to all typography.

```json
{
  ...
  "styles": {
    "typography": {
      "fontFamily": "var(--wp--preset--font-family--system-font)"
    }
  }
  ...
}
```

Once you've made these changes, your updated theme.json file looks like this:

```json
{
	"version": 2,
	"$schema": "https://schemas.wp.org/trunk/theme.json",
	"settings": {
		"typography": {
			"fontFamilies": [
				{
					"fontFamily": "-apple-system,BlinkMacSystemFont,\"Segoe UI\",Roboto,Oxygen-Sans,Ubuntu,Cantarell,\"Helvetica Neue\",sans-serif",
					"name": "System Font",
					"slug": "system-font"
				}
			]
		}
	},
	"styles": {
		"typography": {
			"fontFamily": "var(--wp--preset--font-family--system-font)"
		}
	}
}
```

Now switch back to your Site Editor, and take a look at any of the templates. You should see that the font has been updated to the system font.

## Block Course Theme Settings and Styles

The process outline above is the same for any setting or style you want to apply to your theme.

- Add the relevant setting to the `settings` section in `theme.json`
- Apply the setting via the Global Styles interface OR add it to the relevant style in the `styles` section of the theme.json file.

Styles can be applied globally, as we did for the typography, or to specific blocks.



> **Note**
> To speed up this process, it's also possible to copy exiting settings and styles from existing themes, and update the values to match your theme.

For the purposes of this lesson, we've gone ahead and done some of the groundwork for you, so go ahead and copy the following base `theme.json`, which is based on the Twenty Twenty Three Figma designs, and paste it over your current `theme.json`

```json
{
  "$schema": "https://schemas.wp.org/trunk/theme.json",
  "version": 2,
  "settings": {
    "appearanceTools": true,
    "color": {
      "palette": [
        {
          "color": "#FFF5E1",
          "name": "Base",
          "slug": "base"
        },
        {
          "color": "#781C68",
          "name": "Contrast",
          "slug": "contrast"
        }
      ]
    },
    "layout": {
      "contentSize": "650px",
      "wideSize": "1000px"
    },
    "spacing": {
      "spacingScale": {
        "operator": "+",
        "increment": 0.5,
        "steps": 9,
        "mediumStep": 1.5,
        "unit": "rem"
      },
      "units": [
        "%",
        "px",
        "em",
        "rem",
        "vh",
        "vw"
      ]
    },
    "typography": {
      "dropCap": false,
      "fluid": true,
      "fontFamilies": [
        {
          "fontFamily": "-apple-system,BlinkMacSystemFont,\"Segoe UI\",Roboto,Oxygen-Sans,Ubuntu,Cantarell,\"Helvetica Neue\",sans-serif",
          "name": "System Font",
          "slug": "system-font"
        }
      ],
      "fontSizes": [
        {
          "size": "1rem",
          "slug": "small"
        },
        {
          "size": "1.125rem",
          "slug": "medium"
        },
        {
          "size": "1.75rem",
          "slug": "large"
        },
        {
          "size": "2.25rem",
          "slug": "x-large"
        },
        {
          "size": "2.75rem",
          "slug": "xx-large"
        }
      ]
    }
  },
  "styles": {
    "color": {
      "background": "var(--wp--preset--color--base)",
      "text": "var(--wp--preset--color--contrast)"
    },
    "elements": {
      "button": {
        "border": {
          "radius": "0"
        },
        "color": {
          "text": "var(--wp--preset--color--contrast)"
        },
        "typography": {
          "fontSize": "var(--wp--preset--font-size--medium)"
        },
        ":hover": {
          "color": {
            "background": "var(--wp--preset--color--contrast)",
            "text": "var(--wp--preset--color--base)"
          }
        },
        ":focus": {
          "color": {
            "background": "var(--wp--preset--color--contrast)",
            "text": "var(--wp--preset--color--base)"
          }
        },
        ":active": {
          "color": {
            "text": "var(--wp--preset--color--base)"
          }
        }
      },
      "h1": {
        "typography": {
          "fontSize": "3.625rem",
          "lineHeight": "1.2"
        }
      },
      "h2": {
        "typography": {
          "fontSize": "clamp(2.625rem, calc(2.625rem + ((1vw - 0.48rem) * 8.4135)), 3.25rem)",
          "lineHeight": "1.2"
        }
      },
      "h3": {
        "typography": {
          "fontSize": "2.25rem"
        }
      },
      "h4": {
        "typography": {
          "fontSize": "clamp(1.75rem, calc(1.75rem + ((1vw - 0.48rem) * 8.4135)), 1.875rem)"
        }
      },
      "h5": {
        "typography": {
          "fontSize": "var(--wp--preset--font-size--medium)",
          "fontWeight": "700",
          "textTransform": "uppercase"
        }
      },
      "h6": {
        "typography": {
          "fontSize": "var(--wp--preset--font-size--medium)",
          "fontWeight": "400",
          "textTransform": "uppercase"
        }
      },
      "heading": {
        "typography": {
          "fontWeight": "300",
          "letterSpacing": "-0.02rem",
          "lineHeight": "1.4",
          "textTransform": "capitalize"
        }
      },
      "link": {
        "color": {
          "text": "var(--wp--preset--color--contrast)"
        },
        ":hover": {
          "typography": {
            "textDecoration": "underline dashed"
          }
        },
        ":active": {
          "typography": {
            "textDecoration": "none"
          }
        }
      }
    },
    "spacing": {
      "blockGap": "1.5rem",
      "padding": {
        "top": "0px",
        "right": "var(--wp--preset--spacing--30)",
        "bottom": "0px",
        "left": "var(--wp--preset--spacing--30)"
      }
    },
    "typography": {
      "fontFamily": "var(--wp--preset--font-family--system-font)",
      "fontSize": "var(--wp--preset--font-size--medium)",
      "lineHeight": "1.6"
    }
  }
}
```

## Exporting Styles Applied in the Global Styles Interface

At this point you might be wondering if it's possible to view the code for the styles applied in the Global Styles interface, in the same way you can view the code for the templates and template parts.

Due to the nature of JSON vs HTML/block code, it's not currently possible. What you can do however is use the Overwrite option of the Create Block Theme plugin, which will update your theme.json file with anny changes applied in the Global Styles interface.

If you do follow this process, note that the Create Block Theme plugin will write your theme.json top level elements in alphabetical order, which may not be the order you want. This won't break the functionality of the theme, but it may be a little confusing if, for example, you're used to seeing the `schema` and `version` items at the top of the file.