# Module Quiz

Q. What table in the WordPress database is used to store changes to the global styles, templates, and template parts
1. wp_posts
2. wp_postmeta
3. wp_options
4. wp_theme_mods

Q. What is the value of the post_type field when storing global styles changes?
1. wp_global_styles
2. wp_template_part
3. wp_template

Q. True or false: The entire JSON object that represents the updated Global Styles is stored for the `wp_global_styles` custom post type record.
1. False

Q. True or false: The entire block markup of a template or template part is stored for the `wp_template` or `wp_template_part` custom post type record.
1. True

Q Which of the following actions are taken when a theme is exported from the Site Editor, or using Create Block Theme
1. Checks if the current user has the `edit_theme_options` capability
2. Adds a copy of all the files in the active themes root directory to the Zip archive
3. Runs through all active theme templates and template parts, and creates the relevant file in the Zip archive
4. Generates the settings and styles JSON object, converts it to a theme.json file, and adds it to the Zip archive
5. All of the above
