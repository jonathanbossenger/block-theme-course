# Internationalization in Block Themes

## What is Internationalization?

Internationalization is the process of developing your theme in a way that any human readable text that forms part of your theme can easily be translated into other languages. Internationalization is often abbreviated as i18n (because there are 18 letters between the letters i and n).

Internationalization is done by using a translation function (or set of translation functions) to wrap all translatable text in your application. 

> **Info**
> Translatable text is the human readable text that forms part of a theme. So things like labels, help text, error messages, etc. This does not include your website's content, as this is separate from your theme.

Here is a quick example of a translation function used to make an English string translatable.

```php
__( 'Copyright', 'theme-textdomain' )
```

All translation functions will accept the string to be translated, and the theme's textdomain is parameters.

> **Info**
> The textdomain allows translatable strings to be grouped together under the same domain. 

The translation function for a specific piece of text will look up the translated text for the current language and return it. If no translation is found, it will return the original text.

The process of translating the text is called localization. Localization is often abbreviated as l10n (because there are 10 letters between the letters l and n).

WordPress is used all over the world, by people who speak many different languages. As a developer, you may not be able to provide localization for all your users; however, if you implement the translation function(s) in your code, a translator can successfully localize your code without needing to modify the source code itself.

This module will not teach you the details of how to make your theme translatable, but will show you how to use the translation functions in your block theme. 

You can read more about theme internationalization and localization in the [WordPress Developer Handbook](https://developer.wordpress.org/apis/handbook/internationalization/). You can also read more about the translation functions available to WordPress in the [WordPress Internationalization Documentation](https://developer.wordpress.org/apis/handbook/internationalization/internationalization-functions/).

## Internationalization functions are PHP only

The important thing to remember about internationalization functions for block themes is that they are all PHP functions. So this means that you need to be able to use PHP in your block theme to make theme text translatable.

Can you remember a way you've learned to implement PHP code in a block theme? That's right, Block Patterns!

