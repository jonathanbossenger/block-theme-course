# Block Theme Template Parts

[Short video covering this lesson]

Template Parts are the reusable theme files. Unlike templates, template parts are not rendered directly, but are instead used inside templates to render specfic content. Consider the header and footer template parts you created in the Create a Block Theme (Low-Code) course. These template parts are used inside the page template to render the same header and footer on all template files.

## Template Parts Location

Template parts are located in a directory called `parts`. Just like template files, they are html files that contain a mix of HTML and block markup. 

By default, WordPress block themes expect at least a header and footer template part, but you can create multiple template parts, and use them anywhere in your theme templates.

## Creating New Templates

Just like you did with creating a new Page template, you can also create new template parts from the Site Editor. The difference here is that you define the template part by giving it a name, and then choosing what type of template part it is.

Create a new template by navigating to the Editor. Toggle the Editor navigation menu, and select Template Parts.

[Image of the list of template parts in the Editor created in the previous course]

Click on the Add New button to create a new template part. The Editor will ask you to give the template part a name, and select to either create a general template part, a header template part or a footer template part. 

[Image of the new template part UI]

Create a new General template and call it `quote`. You'll be taken straight to the new Template Part in the editor.

[Image of the new template part in the editor]

Now, add a Quote block, either by clicking the Block Inserter button, or by typing `/quote` in the editor.

Enter an interesting quote, and add the author of the quote as the citation

[Iamge of the quote block with the quote and citation]

Then, select Layout in the Block Sidebar, and enter a padding value of 50px.

[Image of the quote block with the padding value set to 50px]

Now that you have designed your template part, export it to a template part file, as you did for the page template in the previous lesson.

1. View the Code Editor
2. Copy the block code
3. Navigate to the theme directory in your code editor and create a new template part in the `parts` directory called quote.html
4. Refresh the Site Editor, and view the list of template parts

[Image of the list of template parts in the editor]

