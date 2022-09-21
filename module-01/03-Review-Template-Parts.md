# Block Theme Template Parts

[Use template parts](https://videopress.com/v/1FTYZp6a)

Template Parts are reusable parts of a theme. Unlike templates, template parts are not rendered directly, but are instead used inside templates to render specfic content. Template parts of very similar to blocks, in that they are reusable pieces of content that can be inserted into multiple places.

If you completed the Create a Block Theme (Low-Code) course you would have created a header and footer template part. These template parts are used inside the page template to render the same header and footer on all template files.

## Creating Template Parts

Just like you did with creating a new Page template, you can also create new template parts from the Site Editor. The difference here is that you define the template part by giving it a name, and then choosing what type of template part it is.

Create a new template part by navigating to the Editor. Toggle the Editor navigation menu, and select **Template Parts**.

![Template parts](/images/module-01/lesson-03/editor-template-parts.png)

> Click on the Add New button to create a new template part. 

The Editor will ask you to give the template part a name, and select to either create a general template part, a header template part or a footer template part. 

![Adding a header template part](/images/module-01/lesson-03/editor-header-template-part.png)

Go ahead and create a header template part for your theme.

> Create a new header template part, and name it `Header`.

Once the template part is created, you'll be taken straight to the new template part in the editor.

![Editing the header template part](/images/module-01/lesson-03/editor-edit-header-template-part.png)

Now you can begin designing your header template part.

> 1. Add a Column block, with a 3 column layout
> 2. Add a Site Title block to the first column
> 3. Add a Site Logo block to the second column
> 4. Add a Navigation block to the third column

You should end up with a template part that looks something like this.

![Header template part content](/images/module-01/lesson-03/editor-header-template-part-content.png)

Save the template part. You can now use this template part in your page template.

> Now create a footer template part for your theme, and add some content of your own.

## Using Template Parts in Templates

Now that you've created a header and footer template part, you will want to use them in your templates. Adding the template part code to a template in the Site editor is the same as adding any block element. 

Navigate back to your list of templates, and click on the index template to edit it. Then add the header and footer template parts to the template. 

> 1. Click on the Block Inserter, and search for the **Template Part** block
> 2. Add the template part block to your template, and move it into the desired location
> 2. Click the **Choose** button in the template part block to choose the template part
> 4. Choose either the header or footer template part to insert it into the template

Once you have added your template parts, switch to the Code editor view to see the block markup for the template part inside the template.

```html
<!-- wp:template-part {"slug":"header","theme":"new-block-theme"} /-->
...
<!-- wp:template-part {"slug":"footer","theme":"new-block-theme"} /-->
```

Notice that the template-part block accepts the slug of the template part as an attribute, as well as the slug of the theme. 

### Further Reading

You can read more about the [block theme template parts](https://developer.wordpress.org/themes/block-themes/templates-and-template-parts/) in the Theme Handbook.

Now that we've covered creating and editing templates and template parts in the editor, let's look at the options for exporting them to theme files.