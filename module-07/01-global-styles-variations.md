# Global Styles Variations

One of the big benefits of block themes for users is the ease at which they can customize their theme. One of the ways that theme developers can help users with this process is to offer Global Styles variations for the theme. Global Styles variations allow developers to offer a set of additional predefined styles for a theme. These variations can be anything from simply a different set of theme colors to applying additional fonts or specific theme settings. The user can then choose from these styles to customize their theme. 

## How Twenty Twenty-Three uses Global Styles Variations

One of the reasons we chose Twenty Twenty-Three as the "example" theme for this course, is that it's the first theme of it's kind. As it's described in the [proposal post](https://make.wordpress.org/design/2022/07/19/proposal-a-new-kind-of-default-theme/), Twenty Twenty-Three is essentially a stripped back, minimal version of Twenty Twenty-Two which offers a blank canvas to let a diverse range of style variations shine. Released as the new default theme for WordPress 5.9, Twenty Twenty-Three shops will 11 unique Global Styles variations.

![Twenty Twenty-Three Global Styles variations](https://learn.wordpress.org/files/2022/11/global-styles.gif)

## How Global Styles Variations Work

A Global Styles variation is essentially a theme.json file, with a different file name, and stored in a different location. More specifically, they are stored in a directory called `styles`.

You can view all the styles for Twenty Twenty-Three in the theme's [GitHub repository](https://github.com/WordPress/twentytwentythree/tree/trunk/styles).

If you open any of the .json files, you'll see it uses exactly the same format as theme.json, including the same properties and values. The only difference is that a variation file has a `title` property. This indicates the human-readable title of the variation, which is displayed when browsing the variations in the Global Styles interface.

Below is the JSON for the aubergine.json style:

```json
{
  "$schema": "https://schemas.wp.org/trunk/theme.json",
  "version": 2,
  "title": "Aubergine",
  "settings": {
    "color": {
      "gradients": [
        {
          "gradient": "linear-gradient(180deg, var(--wp--preset--color--secondary) 0%,var(--wp--preset--color--base) 100%)",
          "name": "Secondary to Base",
          "slug": "secondary-base"
        },
        {
          "gradient": "linear-gradient(180deg, var(--wp--preset--color--base) 0 min(24rem, 10%), var(--wp--preset--color--secondary) 0% 30%, var(--wp--preset--color--base) 100%)",
          "name": "Base to Secondary to Base",
          "slug": "base-secondary-base"
        },
        {
          "gradient": "linear-gradient(90deg, var(--wp--preset--color--tertiary) 5.74%, var(--wp--preset--color--primary) 100%);",
          "name": "Tertiary to Primary",
          "slug": "tertiary-primary"
        },
        {
          "gradient": "linear-gradient(90deg, var(--wp--preset--color--primary) 5.74%, var(--wp--preset--color--tertiary) 100%);",
          "name": "Primary to Tertiary",
          "slug": "primary-tertiary"
        }
      ],
      "palette": [
        {
          "color": "#1B1031",
          "name": "Base",
          "slug": "base"
        },
        {
          "color": "#FFFFFF",
          "name": "Contrast",
          "slug": "contrast"
        },
        {
          "color": "#FF746D",
          "name": "Primary",
          "slug": "primary"
        },
        {
          "color": "#551C5E",
          "name": "Secondary",
          "slug": "secondary"
        },
        {
          "color": "#FB326B",
          "name": "Tertiary",
          "slug": "tertiary"
        }
      ]
    },
    "typography": {
      "fontSizes": [
        {
          "fluid": {
            "min": "0.875rem",
            "max": "1rem"
          },
          "size": "1rem",
          "slug": "small"
        },
        {
          "fluid": {
            "min": "1rem",
            "max": "1.125rem"
          },
          "size": "1.125rem",
          "slug": "medium"
        },
        {
          "size": "1.75rem",
          "slug": "large",
          "fluid": false
        },
        {
          "size": "3.25rem",
          "slug": "x-large",
          "fluid": false
        },
        {
          "size": "10rem",
          "slug": "xx-large",
          "fluid": {
            "min": "4rem",
            "max": "20rem"
          }
        }
      ]
    }
  },
  "styles": {
    "blocks": {
      "core/comment-reply-link": {
        "elements": {
          "link": {
            "color": {
              "text": "var(--wp--preset--color--primary)"
            },
            "typography": {
              "fontStyle": "italic"
            }
          }
        }
      },
      "core/group": {
        "border": {
          "color": "var(--wp--preset--color--primary)"
        }
      },
      "core/navigation": {
        "typography": {
          "fontSize": "var(--wp--preset--font-size--medium)"
        }
      },
      "core/post-author": {
        "color": {
          "text": "var(--wp--preset--color--primary)"
        },
        "typography": {
          "fontStyle": "italic"
        }
      },
      "core/post-content": {
        "elements": {
          "link": {
            "color": {
              "text": "var(--wp--preset--color--primary)"
            }
          }
        }
      },
      "core/post-date": {
        "elements": {
          "link": {
            "color": {
              "text": "var(--wp--preset--color--contrast)"
            },
            "typography": {
              "letterSpacing": "0.09rem",
              "textTransform": "uppercase"
            }
          }
        }
      },
      "core/post-terms": {
        "elements": {
          "link": {
            "color": {
              "text": "var(--wp--preset--color--primary)"
            },
            "typography": {
              "fontStyle": "italic"
            }
          }
        }
      },
      "core/post-title": {
        "elements": {
          "link": {
            ":active": {
              "color": {
                "text": "var(--wp--preset--color--contrast)"
              }
            }
          }
        },
        "typography": {
          "fontSize": "clamp(2.625rem, calc(2.625rem + ((1vw - 0.48rem) * 8.4135)), 3.25rem)"
        }
      },
      "core/query": {
        "elements": {
          "h3": {
            "color": {
              "text": "var(--wp--preset--color--primary)"
            },
            "typography": {
              "fontSize": "var(--wp--preset--font-size--large)",
              "fontWeight": "700"
            }
          },
          "link": {
            "color": {
              "text": "var(--wp--preset--color--primary)"
            }
          }
        }
      },
      "core/separator": {
        "color": {
          "text": "var(--wp--preset--color--primary)"
        }
      },
      "core/site-title": {
        "border": {
          "color": "var(--wp--preset--color--primary)",
          "style": "solid",
          "width": "0 0 2px 0"
        },
        "elements": {
          "link": {
            ":active": {
              "color": {
                "text": "var(--wp--preset--color--primary)"
              }
            },
            ":focus": {
              "color": {
                "text": "var(--wp--preset--color--primary)"
              },
              "typography": {
                "textDecoration": "none"
              }
            },
            ":hover": {
              "color": {
                "text": "var(--wp--preset--color--primary)"
              },
              "typography": {
                "textDecoration": "none"
              }
            }
          }
        },
        "typography": {
          "letterSpacing": "0.09rem",
          "textTransform": "uppercase"
        }
      }
    },
    "color": {
      "gradient": "var(--wp--preset--gradient--base-secondary-base) no-repeat"
    },
    "elements": {
      "button": {
        "border": {
          "radius": "99999px"
        },
        "color": {
          "gradient": "var(--wp--preset--gradient--tertiary-primary)",
          "text": "var(--wp--preset--color--base)"
        },
        ":hover": {
          "color": {
            "background": "var(--wp--preset--color--primary)",
            "gradient": "none",
            "text": "var(--wp--preset--color--secondary)"
          }
        },
        ":focus": {
          "color": {
            "background": "var(--wp--preset--color--primary)",
            "gradient": "none",
            "text": "var(--wp--preset--color--secondary)"
          }
        },
        ":active": {
          "color": {
            "background": "var(--wp--preset--color--primary)",
            "gradient": "none",
            "text": "var(--wp--preset--color--secondary)"
          }
        },
        ":visited": {
          "color": {
            "text": "var(--wp--preset--color--base)"
          }
        }
      },
      "heading": {
        "typography": {
          "letterSpacing": "-0.019rem"
        }
      },
      "link": {
        ":active": {
          "color": {
            "text": "var(--wp--preset--color--primary)"
          }
        }
      }
    },
    "typography": {
      "fontFamily": "var(--wp--preset--font-family--dm-sans)"
    }
  }
}
```

To create a Global Styles variation, you only need to create the json file in the `styles` directory, and WordPress will detect it and make it available in the Global Styles sidebar. You're not required to register it anywhere else in the theme.

You also don't need to include every single property from the original theme.json file in the variation. For example, if you're just adding a new color selection for the theme background and text, you can just include that in the variation file. The rest of the properties will be inherited from the original theme.json file.

In the next lesson, you'll learn how to create a Global Styles variation for your theme, by editing the Global Styles in the editor, and then exporting the variation to a file.




