# Create a Global Style Variation

## Design a Global Style Variation in the Site Editor

Because it's possible to edit Global Styles in the Site Editor, a quick way to start designing a new variation is to start making changes in the Editor.  This is a great way to get a feel for how the variation works, before saving it as a variation file.

In this lesson, you're going to create a dark theme variation for your new block theme. The colours you'll be applying to the variation are the following:

- Background color: #263238
- Text color: #c3e88d
- Links and Headings color: #c792ea

Go ahead and apply these colors to your theme in the Site Editor, starting with the background.  

1. Navigate to the Site Editor, and open the Global Styles Interface
2. Select **Colours** and then **Background**.  
3. Click on the rectangle that indicates the current background color
4. In the Hex color text area, #263238. This should select and apply the dark grey color.

Now apply the alternative colours to the Text as well as the Links and Headings style elements. Your dark theme style should look something like this:

![Dark theme style](/images/module-07/lesson-02/dark-theme-style.png)

Go ahead and save this to the Global Styles in the database.

## Save the Global Style Variation to a variation file.

As we learned in the lesson on saving global styles to the database from part 1 of the Developers Guide to Block Themes, the saved Global Style changes are stored in the `wp_posts` table, as a `wp_global_styles` custom post type, in the `post_content` field.  


```json
{
  "styles": {
    "color": {
      "background": "#263238",
      "text": "#c3e88d"
    },
    "elements": {
      "link": {
        "color": {
          "text": "#c792ea"
        }
      },
      "heading": {
        "color": {
          "text": "#c792ea"
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
      "background": "#263238",
      "text": "#c3e88d"
    },
    "elements": {
      "link": {
        "color": {
          "text": "#c792ea"
        }
      },
      "heading": {
        "color": {
          "text": "#c792ea"
        }
      }
    }
  },
  "settings": [],
  "version": 2
}
```

The last step is to clear out the saved Global Styles customisations in the database, so that the theme switches back to its default settings.

1. Click on the tree dots on the top right of the Global Styles interface and select **Reset to defaults**.
2. Save the changes.

Now, refresh the Site Editor, and the option to **Browse Styles** will appear in the Global Styles interface.  You can now choose between your default style, and the new Dark Theme style.

## Create the Global Style Variation Using Create Block Theme

It is also possible to use the Create Block Theme's ***Create a style variation*** option to create the style variation file from the saved global styles. This saves all the manual work of copying the saved JSON from the database, and creating the style variation file. To start, delete the `styles` directory you just created, and then recreate the color changes in the Site Editor from the Design a Global Style Variation in the Site Editor.

1. Delete the newly created `styles` directory
2. Refresh the Site Editor, and open the Global Styles Interface
3. Select **Colors** and then set the **Background**, **Text**, **Links**, and **Headings** colors
4. Save the new Global Styles to the database

Now, in the Create Block Theme interface, select the **Create a style variation** option. The page will give you an option to give the variation a name, which it will slugify and use to create the variation file. In this case, if you enter "Dark Theme" in the name field, it will create a `dark-theme.json` file in the `styles` directory.

The two main differences between the `dark-theme.json` file created by the Create Block Theme interface, and the one you created manually, are that you still need to add the title attribute, and the one generated using Create Block theme contains a full copy of the original theme.json file, with the changes saved to the database updated in the variation file. 
