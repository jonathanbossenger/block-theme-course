# Saving Changes to Global Styles

One of the benefits of developing a block theme in the Site Editor, is that you can make changes and see how they would affect the design, without writing them to any theme files, or needing to refresh your browser. 

This is because any changes you make to the Global Styles are saved to the WordPress database, and are only read from the database when the site is rendered in the browser.

It is important to understand where these changes are saved, as well as how WordPress decides which styles to use, when rendering the site.

## Where are Global Styles saved?

When you make changes to theme styles in the Global Styles interface, and hit **Save**, the changes are saved to the `wp_posts` table in the WordPress database. Global Styles are stored as a specific custom post type. 

Below is a breakdown of the important fields and the data that is stored for changes made to a theme's Global Styles.

 - `post_content`: stores the updated Global Styles data, in JSON format
 - `post_title`: stores a value of "Global Styles"
 - `post_name`: stores the slug of the post as "wp-global-styles-{theme-slug}", where {theme-slug} is the slug of the active theme
 - `post_type`: stores the post type as "wp_global_styles"

Go ahead and make some changes to your theme's Global Styles in the Editor, and save them.

> **Do:**
> 1. Set the global Background colour to the Page pink preset
> 2. Set the global Text colour to the Black preset 
> 3. Change the Content and Wide dimensions in the global Layout settings to 750px and 1200px respectively

![Making changes in the Editor](/images/module-03/lesson-01/global-styles-changes.gif)

Once you've saved the changes, open the database in your favorite database management tool (e.g. [phpMyAdmin](https://www.phpmyadmin.net/), [TablePlus](https://tableplus.com/) etc). 

Search in the `wp_posts` table for a record with a `post_name` of `wp-global-styles-new-block-theme` and `post_type` of `wp_global_styles`.

If your database management tool supports running a SQL query, you can also run this query:

```mysql
SELECT post_content, post_title, post_name, post_type FROM `wp_posts` WHERE post_type = 'wp_global_styles' and post_name = 'wp-global-styles-new-block-theme'
```

Here are the results of that search in TablePlus:

![Global Styles](/images/module-03/lesson-01/global-styles-view-tableplus.png)

If you look at the post_content field, you can see the styles are stored as JSON data.

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
      "wideSize": "1200px"
    }
  },
  "isGlobalStylesUserThemeJSON": true,
  "version": 2
}
```

Take note of the following:

1. Only the changes are stored, not an updated version of the original theme.json with the changes included.
2. The style values are stored in a slightly different format to what you've seen in the theme.json file so far (e.g. `var:preset|color|pale-pink` instead of `var(--wp--preset--color--pale-pink)`). Both formats are acceptable.
3. The `isGlobalStylesUserThemeJSON` field is included in the stored data, and set to `true`. This allows WordPress to know which styles are from the theme.json file, and which are from the stored Global Styles data.

## How WordPress Decides Which Global Styles to use

When a post or page is rendered, WordPress will first load all the settings and styles from the theme.json file, and then merge any settings or styles stored in the `wp_global_styles` custom post type record.

What is also important to understand is that if you make changes to a setting or style in theme.json, and there's also a value for that setting or style in the custom post type record, then the value from the custom post type record will be used, and not the value from theme.json. 

If you manually make changes to the theme.json file, you can reset the theme styles in the Global Styles interface. To do this, click on the tree dots in the Global Styles interface, to open the options menu, and select **Reset to defaults**.

![Reset Global Styles](/images/module-03/lesson-01/reset-global-styles.png)

> **Do:** Go ahead and reset the Global Styles now.

This will delete the custom post type record, and the theme styles will be loaded from the theme.json file.

