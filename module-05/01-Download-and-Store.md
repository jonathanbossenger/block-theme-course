# How to Download a Web Font and Store It in the Theme

WordPress 5.9 introduced the ability for theme authors to bundle custom fonts and make them available via the block system.  This makes them available via global styles and on a per-block level.

## Downloading a Web Font

There are many sites around the web to download custom web fonts from.  Google Fonts is a common place for theme authors, so we will use it throughout this lesson.

To get started, head over to the [Google Fonts](https://fonts.google.com/) website and browse for a font as shown in the following screenshot:

![Google Fonts homepage, which lists a grid of font selections.](https://learn.wordpress.org/files/2022/11/google-fonts.png)

For this lesson, we have selected the [Open Sans font](https://fonts.google.com/specimen/Open+Sans).  It is one of the most popular choices from Google Fonts.

The next step for getting the Open Sans or a font family of your choice into your theme is to click the **Download Family** button on the font's page, as shown in the following screenshot:

![Open Sans family on the Google Fonts website. The "Download Family" button is highlighted.](https://learn.wordpress.org/files/2022/11/google-fonts-download.png)

Once downloaded, unzip the `Open_Sans.zip` file using your preferred utility on your computer.  You will see several files in the folder.  However, you will only need the following two:

- `/Open_Sans`
	- `/OpenSans-Italic-VariableFont_wdth,wght.ttf`
	- `/OpenSans-VariableFont_wdth,wght.ttf`

Because Open Sans is a variable font that supports a range of weights, you do not need all of the extra files from the `/Open_Sans/static` folder.

Unfortunately, the downloaded Open Sans files are in `.ttf` format.  When downloading fonts online, you may not get the ideal file format for serving images over the web.  Often, as is the case here, you are likely to receive `.ttf` files.  These can have large file sizes and slow down page speeds.  These should be converted to `.woff2` and/or `.woff` format.  There are various converter scripts and apps available online, such as [Google Webfonts Helper](https://google-webfonts-helper.herokuapp.com/fonts).

`.woff2` is the preferred file format. All modern browsers support it, and its can often save 50% or more over other formats.  If you need to support IE 9 - 11, you should also include the `.woff` format.  You can see which browsers support various formats via the [Can I use...](https://caniuse.com) website.

One you've converted the fonts, you should have a folder that looks like the following (delete the `.ttf` files if you're not supporting them for old browsers):

- `/Open_Sans`
	- `/OpenSans-Italic-VariableFont_wdth,wght.woff2`
	- `/OpenSans-VariableFont_wdth,wght.woff2`

You may rename these files to anything you prefer if it helps with remembering them.  For the purposes of this lesson, we'll keep them the same.

## Storing the Web Font in the Theme

The next step is to figure out where the font files should go in your theme.  Every theme author has their preference for organizing such files, but the recommended location is within an `/assets/fonts` folder.  The easiest way to do that is to copy over the contents of the `Open_Sans` folder and drop it in, so that your theme's directory structure looks like the following:

```
theme-slug
	/...
	/assets
		/fonts
			/OpenSans-Italic-VariableFont_wdth,wght.woff2
			/OpenSans-VariableFont_wdth,wght.woff2
```
