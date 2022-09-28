# Saving Templates and Template Parts

Just like Global Styles, changes to your theme's templates and template parts made the Site Editor are stored as a custom post type in the WordPress database.

## Where are Templates saved?

Similar to Global Styles, templates and template parts are stored as a specific custom post type. Let's look at the important fields and the data that is stored for each.

Templates

- `post_content`: stores the updated Global Styles data, in JSON format
- `post_title`: stores a value of "Global Styles"
- `post_name`: stores the slug of the post as "wp-global-styles-{theme-slug}", where {theme-slug} is the slug of the active theme
- `post_type`: stores the post type as "wp_global_styles"

Template parts