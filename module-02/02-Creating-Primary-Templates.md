# Introduction

As discussed in the last lesson, the primary templates are:
- index
- singular
- archive
- single
- page
- home
- 404
- search

In the recap of templates lesson, you created the index and page templates. Now, you can create the rest of the primary templates in the editor. A good place to start would be the single template, as it would be used for displaying a single post.

## Creating a Primary Template

Creating the single template follows the same process you followed when creating the page template.

> 1. Navigate to the list of templates in the editor
> 2. Click the "Add New" button
> 3. Select the "Single" template from the list

The editor will create the single template, and populate it with a copy of the content from your index template. You can then edit the template to add/remove the content you want to display for a single post. 

For now, you can leave the template as is, save it, and then move on to creating the other primary templates:

- Archive
- Front Page - the home template
- 404
- Search

Once you've created your templates in the editor, you can export your theme templates using one of the export options discussed in a previous lesson.

> Pro Tip. The Overwrite option of the Create Block Theme plugin is very useful here. It allows you to save the changes you've made in the editor to the correct files in the current theme, and clears out any changes stored in the database. This is useful if you want to store your theme changes to a revision control system, like Git.

Which ever option you used to export your template content, your theme directory will start coming together as you build the various templates.

![Theme Structure](/images/module-02/lesson-02/block-theme-primary-templates.png)

## Template Content

The actual template content you add to your templates will depend on the design of your theme. Ideally, you would have designed your theme in something like Figma or Sketch, and have a design for each of the primary templates.

If you're not sure where to get started, check out the [module on designing a theme in the Create a Block Theme Course](#) or take some inspiration from the [open source theme designs](https://make.wordpress.org/design/2022/07/01/open-sourcing-theme-designs/) released by the WordPress design team.

For example, the designs for the [Twenty Twenty Three](https://www.figma.com/community/file/1139275543113752375) theme contain a template design for each of the primary templates, as well as a full style guide, so that you can create a theme that matches the design.