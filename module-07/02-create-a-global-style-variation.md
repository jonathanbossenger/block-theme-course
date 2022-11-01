# Create a Global Style Variation

## Design a Global Style Variation in the Site Editor

Because it's possible to edit Global Styles in the Site Editor, a quick way to start designing a new variation is to start making changes in the Editor.  This is a great way to get a feel for how the variation works, before saving it as a variation file.

In this lesson, you're going to create a dark theme variation for your new block theme. The colours you'll be applying to the variation are the following:

- Background color: #121212
- Text color: #BB86FC
- Links color: #03DA5C

These colors are part of the dark theme colors from the [Material Design](https://m2.material.io/design/color/dark-theme.html) guidelines.

Go ahead and apply these colors to your theme in the Site Editor, starting with the background.  

1. Navigate to the Site Editor, and open the Global Styles Interface
2. Select **Colours** and then **Background**.  
3. Click on the rectangle that indicates the current background color
4. In the Hex color text area, #121212. This should select and apply the dark grey color.

Now apply the alternative colours to the Text and Links style elements. Your dark theme style should look something like this:

![Dark theme style](/images/module-07/lesson-02/dark-theme-style.png)

Go ahead and save this to the Global Styles in the database.

## Save the Global Style Variation to a variation file.

As we learned in the lesson on saving global styles to the database from part 1 of the Developers Guide to Block Themes, the saved Global Style changes are stored in the `wp_posts` table, as a `wp_global_styles` custom post type, in the `post_content` field.  


```json
{
  "styles": {
    "color": {
      "background": "#121212",
      "text": "#bb86fc"
    },
    "elements": {
      "link": {
        "color": {
          "text": "#03da5c"
        }
      }
    }
  },
  "settings": [],
  "isGlobalStylesUserThemeJSON": true,
  "version": 2
}
```

You can use this json file to create the new style, simply by adding the `title` property, and removing the `isGlobalStylesUserThemeJSON` property.

1. Create a new directory in your theme, called `styles`
2. Create a new file called `dark-theme.json` in the `styles` directory
3. Copy the json from the `post_content` field of the `wp_global_styles` custom post type, and paste it into the `dark-theme.json` file.
4. Add a `title` property to the json, and set it to "Dark Theme"
5. Remove the `isGlobalStylesUserThemeJSON` property from the json.

The final JSON in the `styles/dark-theme.json` file should look like this:

```json
{
  "title": "Dark Theme",
  "styles": {
    "color": {
      "background": "#121212",
      "text": "#bb86fc"
    },
    "elements": {
      "link": {
        "color": {
          "text": "#03da5c"
        }
      }
    }
  },
  "settings": [],
  "version": 2
}
```

The last step is to clear out the saved Global Styles customisations in the database, so that the theme switches back to it's default settings.

1. Click on the tree dots on the top right of the Global Styles interface and select **Reset to defaults**.
2. Save the changes.

Now, refresh the Site Editor, and the option to **Browse Styles** will appear in the Global Styles interface.  You can now choose between your default style, and the new Dark Theme style.

## Create the Global Style Variation Using Create Block Theme