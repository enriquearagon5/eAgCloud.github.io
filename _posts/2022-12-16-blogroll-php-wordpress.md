---
published: false
Title: 'How to add a blogroll to a classic WordPress theme, using a PHP script'
layout: post
author: Antonio C.
categories: wordpress
---
If you need a blogroll to add to a classic WordPress theme, in this post I will help you by writing the corresponding PHP code. We will see how you can insert this code in any page of your website, from a .txt file that contains the title, the url of the site and the url of the RSS feed.

This question came up on Mastodon and I wanted to show you the codebase. Of course, you can decorate as much as you want. There is a “blogroll” class to apply CSS and we will assume that the theme used is not a block theme (in a later post, we will see how you can do it in a block theme with the site edit function).

## Plugin to insert the PHP code

We will use the plugin [Insert PHP Code Snippet](https://wordpress.org/plugins/insert-php-code-snippet/) that will be used to write the code and generate a shortcode.

Once installed and active, you will see a new section “XYZ PHP Code” in the left side column of the WordPress control panel.

In the “PHPCode Snippets” section you will see the “Add new PHP Code Snippet” button with which you can write and save the new snippet. Immediately, a shortcode will be associated that you will see in the list of snippets and that you can copy to the clipboard in order to use it.

There will be basically two ways to use said snippet:

- Selecting it within a dropdown that you will see when you drag the corresponding widget to a specific widget area. That widget appears in the widget list when you install the plugin.
- Pasting the shortcode inside the “Shortcode” block, on any page of your WordPress.

## .txt file to configure the blogroll

To configure the blogroll, we will use a .txt text file that we will save inside the wp-content folder.

That file will contain the title, site URL, and RSS feed URL for each entry. For example:

> El País, https://www.elpais.com, https://feeds.elpais.com/mrss-s/pages/ep/site/elpais.com/portada
The World, https://www.elmundo..es, https://e00-elmundo.uecdn.es/elmundo/rss/espana.xml
ABC,https://www.abc.es,https://www.abc.es/rss/feeds/abc_EspanaEspana.xml

## PHP code to display the blogroll

To insert a blogroll into a WordPress page from a text file containing the title, site URL, and RSS feed URL of each post, you can use the following PHP code:

[See the code](https://www.blogpocket.com/2022/12/16/blogroll-tema-clasico-wordpress-mediante-un-script-php/) in this post (in spanish)

If we use the Local app to test this code, and assume we upload it to wp-content, the path to the blogroll.txt file will be:

> /Users/antoniocambronerosanchez/Local Sites/prueba-gutenberg/app/public/wp-content/
You will have to modify the path to the file, in your case.

This code reads the text file line by line and adds each blogroll entry to an HTML list. The esc_url() and esc_html() functions are also used to sanitize the site URL and link title, respectively, before inserting them into the page. In addition, a link with the class "rss-link" is displayed, which leads to the URL of the RSS feed of each site.

## How to add it to any page of your WordPress

Simply edit the page and insert the “Shortcode” block where you want or need to display the blogroll.

You can obtain the Shortcode by going to the “XYZ PHP Code > PHPCode Snippets” section that you will see in the side column of WordPress administrator options.

## How to add it to the Sidebar of your blog

If your classic theme has a widget area -prepared by the theme developer-, simply drag the "Insert PHP Snippet" widget to the area where you want to display the blogroll. This widget is added to the list of available widgets when the Insert PHP Code Snippet plugin is activated.

Once the widget is located (for example in the Footer widget), choose the shortcode from the dropdown and save the changes.

Also, you can create a widget area by following the instructions in our [How to Create an After Entry Widget Area in a Classic WordPress Theme guide](https://blogpocket.github.io/how-to-create-new-widgets-area/).

## Conclusions

We have seen the PHP code to embed in a WordPress page, in order to display a blogroll from a .txt file that contains the title, the url of the site and the url of the RSS feed.

It is a code base that can be altered to your liking and you can place it wherever you want:

- Directly in an HTML file of the classic theme you use.
- On any page of your WordPress, using the shortcode corresponding to the Insert PHP Code Snippet plugin.
- In an existing widget area, within the theme.
