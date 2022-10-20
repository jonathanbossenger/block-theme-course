# Saving Templates and Template Parts

Just like Global Styles, changes to your theme's templates and template parts made the Site Editor are stored as a custom post type in the WordPress database.

## Where are Templates saved?

Similar to Global Styles, templates and template parts are stored as a specific custom post type. Let's look at the important fields and the data that is stored for each.

### Template parts

- `post_content`: stores the full template part content, in HTML format, including block markup
- `post_title`: stores the name of the template part
- `post_name`: stores the slug of the template part
- `post_type`: stores the post type as "wp_template_part"

### Templates

- `post_content`: stores the full template content, in HTML format, including block markup
- `post_title`: stores the name of the template
- `post_name`: stores the slug of the template
- `post_type`: stores the post type as "wp_template"

### Example

Go ahead and make some changes to your theme's header template part, and save it.

> **Do:** Select the Site Title in the header template part, and change the Typography size to Medium

Once you've saved the changes, open the database in your favorite database management tool (e.g. [phpMyAdmin](https://www.phpmyadmin.net/), [TablePlus](https://tableplus.com/) etc).

Search in the `wp_posts` table for a record with a `post_name` of `header` and `post_type` of `wp_template_part`.

If your database management tool supports running a SQL query, you can also run this query:

```mysql
SELECT post_content, post_title, post_name, post_type FROM `wp_posts` WHERE post_type = 'wp_template_part' and post_name = 'header'
```

> **Note:** Depending on how your template part is named, you may need to change the `post_name` value. Alternatively, just search for any `wp_template_part post` types.

Here are the results of that search in TablePlus, with the header template part selected:

![Template Parts](https://learn.wordpress.org/files/2022/10/template-parts-view-tableplus.png)

## Template/Template Parts Relationship to the Theme

In the previous lesson on saving Global Styles, you learned that the global style record uses a post_name value which includes the theme slug. This allows WordPress to determine which saved styles to use for which theme.

The same is not true for templates and template parts, as the post_name value is the name of the template or template part. Instead, the relationship between the template/template part and the theme is stored using the WordPress taxonomies system. This is the same system that manages the relationship between posts and categories or tags.

It's a bit more complicated to explain how this system works in the context of this lesson, but rest assured that it works behind the scenes to make sure the saved templates and template parts are associated to the correct theme

## Resetting Templates and Template Parts

Just as you can with Global Styles, you can reset the changes saved to a template or template part. To do this, click on the **Show template details** button and select **Clear customizations**

![Reset Template Customizations](https://learn.wordpress.org/files/2022/10/clear-template-customisations.gif)

This will delete the custom post type record, and the template layout will be loaded from the template file.

