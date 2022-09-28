# Saving Changes to Global Styles

One of the benefits of developing a block theme in the Site Editor, is that you can make changes and see how they would affect the design, without writing them to any theme files, or needing to refresh your browser.

This is because any changes you make to the Global Styles are saved to the database, and are only read from the database when the site is rendered to the browser.

It is important to understand where these changes are saved, as well as how WordPress decides which styles to use, when rendering the site.

## Where are Global Styles saved?

When you make changes to the Global Styles, they are saved to the database in the `wp_posts` table, as a custom post type. 

Below is a detailed breakdown of the relevant data that is stored for any changes made to a theme's Global Styles, and stored in the database.

 - post_content: stores the updated Global Styles values, in JSON format
 - post_title: stores the name of post as "Global Styles"
 - post_name: stores the slug of the post as "wp-global-styles-{theme-slug}"
 - post_type: stores the post type as "wp_global_styles"

Make some changes to your theme's Global Styles in the editor, save them, and then open the database in your favorite database management tool. 

Search in the wp_posts table for a record with a `post_name` of `wp-global-styles-new-block-theme` and `post_type` of `wp_global_styles`.

If your database management tool 

```mysql
SELECT post_content, post_title, post_name, post_type FROM `wp_posts` WHERE post_type = 'wp_global_styles' and post_name = 'wp-global-styles-new-block-theme'
```


## How WordPress decides which styles to use

In the example below, the following settings have been changed in the Global Styles interface in the editor, and saved to the database

- set the global background colour to the page-pink preset
- set the global text colour to the black preset
- set the contentSize to 750px and the wideSize to 1000px

```json
{
  "styles": {
    "color": {
      "background": "var:preset|color|pale-pink",
      "text": "var:preset|color|black"
    }
  },
  "settings": {
    "layout": {
      "contentSize": "750px",
      "wideSize": "1000px"
    }
  },
  "isGlobalStylesUserThemeJSON": true,
  "version": 2
}
```

You will notice that only the changes are stored as JSON in the custom post type record, along with a special `isGlobalStylesUserThemeJSON` property, which is set to `true`. 

When a post or page is rendered, WordPress will first load all the settings and styles from the theme.json file, and then merge any settings or styles stored in the custom post type record.

What is also important to understand is that if you make changes to a setting or style in theme.json, and there's also a value for that setting or style in the custom post type record, then the value from the custom post type record will be used, and not the value from theme.json. 