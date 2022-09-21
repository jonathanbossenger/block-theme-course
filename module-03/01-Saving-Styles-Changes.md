# Introduction

One of the features of block themes is the [theme.json](https://developer.wordpress.org/block-editor/how-to-guides/themes/theme-json/) file. In a block theme, theme.json allows the theme developer to control 2 things:

1. Toggling theme settings
2. Adding or setting theme styles

While it is currently only possible to toggle theme settings in the theme.json file, it is also possible to enable theme styles via the Global Styles interface.

When saving these theme styles in the editor, the changes are not stored back to the theme.json file, but instead stored in the database. This means that if you are developing a theme for distribution, you need to know where the theme styles are stored, and how to export them to the theme.json file.

# Creating new Global Styles

To start with, create a new custom color 