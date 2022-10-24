# Exporting a Theme

Now that you understand how changes to Global Styles, templates and template parts are stored in the database, let's take a look at what happens behind the scenes, when you export the theme.

## Site Editor Export

When you export the theme from the Site Editor, a request is made to to the `wp-block-editor/v1/export` WP REST API endpoint, which runs the export. The main function that handles the export is [wp_generate_block_templates_export_file](https://developer.wordpress.org/reference/functions/wp_generate_block_templates_export_file/). This process performs the following actions:

1. Checks it the current user has the `edit_theme_options` capability
2. Creates a new Zip archive in memory, with a templates and template parts directory
3. Adds a copy of all the files in the active themes root directory to the Zip archive
4. Runs through all active theme templates and template parts, and creates the relevant file in the Zip archive
   1. It first looks for a template/part in the database, and creates the file from the saved data
   2. If it cannot find a template/part in the database, it will look for one in the active themes templates directory
5. Generates the settings and styles JSON object, converts it to a theme.json file, and adds it to the Zip archive
   1. It first gets the JSON object from the active themes theme.json file
   2. Next it looks for any Global Styles stored in the database, and merges them with the JSON object
6. Finally, it outputs the Zip archive to the browser, to be saved by the user.

## Create Block Theme Export

The Create Block Theme plugin uses the same core functionality to export the theme. The main difference is in how it exports or creates theme files, based on the option selected. For example, if you choose to create a child theme, it will only export the changes as child theme files, and if you use the Overwrite option, instead of creating a zip file, it will overwrite the relevant theme files with the updates from the database.