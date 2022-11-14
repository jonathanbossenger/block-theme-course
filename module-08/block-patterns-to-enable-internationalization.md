# Using Block Patterns to Enable Internationalization

As you leaned in module x of this course, Block Patterns are a way that you can implement PHP code in a block theme. In the section on Adding Images and Other Dynamic Data in Patterns, you used a PHP function to add a hero image to the pattern. 

```php
echo esc_url( get_theme_file_uri( 'assets/images/hero-background.webp' ) ); 
```

This means that you can make use of the same PHP support in patterns, and start making any theme text translatable.

## Creating a translatable footer

In this section, you will use a PHP function to make a string translatable.

