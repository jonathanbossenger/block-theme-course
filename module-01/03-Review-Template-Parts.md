# Block Theme Template Parts

The **Template Part** block is frequently used for creating the header and footer of your theme. Template parts are very similar to [synced patterns](https://wordpress.org/documentation/article/reusable-blocks), in that they are reusable pieces of content that can be inserted into multiple places.

For this reason, you will now find your Template Parts within the **Patterns** folder in the Site Editor.

If you completed the [Develop Your First Low-Code Block Theme course](https://learn.wordpress.org/course/develop-your-first-low-code-block-theme/) course you would have created a header and footer template part. These template parts are used inside the page template to render the same header and footer on all template files.

## Creating Template Parts

Just like you did with creating a new Page template, you can also create new template parts from the Site Editor. The difference here is that you define the template part by giving it a name, and then choosing what type of template part it is.

Create a new template part by opening the Patterns folder and selecting **Manage all template parts**.

![Template parts](https://learn.wordpress.org/files/2022/10/editor-template-parts.png)

> **Do:** Click on the **Add New Template Part** button to create a new template part. 

The Editor will ask you to give the template part a name, and select to either create a general template part, a header template part or a footer template part. 

![Adding a header template part](https://learn.wordpress.org/files/2022/10/editor-header-template-part.png)

Go ahead and create a header template part for your theme.

> **Do:** Create a new header template part, and name it `Header`.

Once the template part is created, you'll be taken straight to the new template part in the Editor.

![Editing the header template part](https://learn.wordpress.org/files/2022/10/editor-edit-header-template-part.png)

Now you can begin designing your header template part. You can use **Group** blocks and **Row** blocks to group and align elements in the template part.

> **Do:** 
> 1. Add a **Group** block.
> 2. Inside the **Group** block, add a **Row** block.
> 3. Inside the **Row** block, add a **Site Title** block.
> 4. After the **Site Title** block, add a **Navigation** block.

You should end up with a template part that looks something like this.

![Header template part content](https://learn.wordpress.org/files/2022/10/editor-header-template-part-content.png)

At this point you probably agree that it would be ideal if the navigation were aligned to the right. Fortunately you can achieve this by changing the **Justification** setting on the **Row** block. 

> **Do:** Select the **Row** block, and change the **Justification** setting to **Space between items**.

![Header template part content 2](https://learn.wordpress.org/files/2022/10/editor-header-template-part-content-space.png)

> **Do:** If you can't see the block's **Settings Sidebar** on the right, select the Row block and click on the Settings menu to show the **Settings Sidebar**.

Save the template part. You can now use this template part in your page template.

> **Do:** Save the `Header` template part.

Now create a footer template part for your theme.

> **Do:** Create a `Footer` template part by navigating to the Template Parts list and clicking **Add New Template Part**. Name the template part and choose the Footer location.

Then you can add some content to the footer.

> **Do:**
> 2. Add a **Group** block.
> 3. Add a **Row** block to the **Group** block.
> 4. Add the **Site Title** block to the **Row** block.
> 5. Change the **Site Title** block settings to use a paragraph and not an h1 tag.
> 6. Add a **Paragraph** block next to the **Site Title** block with the text "Proudly powered by WordPress".
> 7. Add a link to the word WordPress in the **Paragraph** block that links to `https://wordpress.org/`.
> 8. Change the **Justification** setting on the **Row** block to "Space between items".

![Footer template part content](https://learn.wordpress.org/files/2022/10/editor-footer-template-part-content.png)

Make sure to save the footer template before moving on.

## Using Template Parts in Templates

Now that you've created a header and footer template part, you will want to use them in your templates. Adding the template part code to a template in the Site Editor is the same as adding any block element. 

Navigate back to your list of templates, and click on the index template to edit it. Then add the header and footer template parts to the template. 

> **Do:**
> 1. Click on the Block Inserter, and search for the **Template Part** block
> 2. Add the **Template Part** block to your template, and move it into the desired location
> 2. Click the **Choose** button in the **Template Part** block to choose the template part
> 4. Choose either the header or footer template part to insert it into the template

Once you have added your template parts, switch to the Code editor view to see the block markup for the template part inside the template.

```html
<!-- wp:template-part {"slug":"header","theme":"new-block-theme"} /-->
...
<!-- wp:template-part {"slug":"footer","theme":"new-block-theme"} /-->
```

Notice that the **Template Part** block accepts the slug of the template part as an attribute, as well as the slug of the theme. 

### Further Reading

You can read more about the [block theme template parts](https://developer.wordpress.org/themes/block-themes/templates-and-template-parts/) in the Theme Handbook. [In this article](https://make.wordpress.org/core/2023/07/13/core-editor-improvement-advancing-the-power-of-patterns), you can learn more about the improvement made to the Site Editor in release 6.3 when reusable blocks became synced patterns. Furthermore, you can learn more in the article about [patterns, template parts, and synced patterns](https://wordpress.org/documentation/article/comparing-patterns-template-parts-and-reusable-blocks).

Now that we've covered creating and editing templates and template parts in the Editor, let's look at the options for exporting them to theme files.