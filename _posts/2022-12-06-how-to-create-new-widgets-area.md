---
published: true
layout: post
title: How to Create an After Entry Widget Area in a WordPress Classic Theme
author: Antonio C.
categories: wordpress
---
In this post you will learn how to create a new after entry widget area (at the end of individual post content) in a WordPress classic theme.

This solves the problem that can occur if you want to [add a Mastodon share button to your blog](https://blogpocket.github.io/wordpress-button-mastodon/) and you have an active classic theme that does not have such an “after entry” widget area.
 
## How do I create a new widget area in WordPress, to place at the bottom of each blog post?

> This section (and only this one, in this article) has been automatically generated using [ChatGPT](https://chat.openai.com/chat). This is purely for experimental purposes in order to test the power of such an amazing AI tool like ChatGPT. Considering that ChatGPT can occasionally generate incorrect information, produce harmful instructions or biased content, and has limited knowledge of the world and events after 2021, the text obtained has been reviewed to be technically consistent with how WordPress works. After this section, you can see how this process is applied in practice to add a new widget area in WordPress.

[Top of ChatGPT answer]

To create a new widget area in WordPress that displays at the bottom of each blog post, you'll need to follow these steps:

Open your WordPress theme's functions.php file and add a new function to register the widget area. 

This function should use the WordPress register_sidebar() function, which takes a set of parameters to customize the widget area.

It uses the WordPress dynamic_sidebar() function in the blog post template file to display the widget area at the bottom of each post.

Customize the placement and layout of the widget area using your WordPress theme's style sheet.
Here's an example of what the function to register the widget area might look like:
 
> function create_widget_area() {
  register_sidebar( array(
    'name' = __( 'My Widget Area', 'textdomain' ),
    'id' = 'my-area-widget',
    'description' = __( 'A description of my widget area.', 'textdomain' ),
    'before_widget' = '<section id="%1$s" class=" widget %2$s"',
    'after_widget' = '</section',
    'before_title' = '<h2 class="widget-title"',
    'after_title' = '</h2' ,
  ) );
}
add_action( 'widgets_init', 'create_widget_area' );
 
In this example, the create_area_widget() function is used to register a widget area with the register_sidebar() function. This function takes a number of parameters to customize the widget area, such as its name, ID, and description. Some default values ​​are also used for the content to be displayed before and after the widget, and before and after the widget title.

Then, in the blog post template file, use WordPress' dynamic_sidebar() function to display the widget area at the bottom of each post:
 
> if ( is_active_sidebar( 'my-widget-area' ) ) {
  dynamic_sidebar( ' my-area-widget' );
}
 
In this example, we check if the widget area is active on the site using the is_active_sidebar() function. If the widget area is active, the dynamic_sidebar() function is used to display the widget area at the location where the function is called in the template file.

[End of ChatGPT reply]
 
## Practical Implementation

We have installed the classic Twenty Twenty One theme on a WordPress 6.1.1 installation and using [the Local app](https://www.blogpocket.com/2021/11/22/crear-web-pruebas-local/).

> In a block theme (such as Twenty Twenty Two or Twenty Twenty Three), which does not have a widget area, you just have to edit the template corresponding to the individual post and insert the element you want. It can be a design made with blocks, a reusable block, a pattern, or even a shortcode associated with an HTML or PHP code (see [How to add a Mastodon share button to your WordPress](https://blogpocket.github.io/wordpress-button-mastodon/)).

The first thing we did is install and activate the [Widget Classic](https://es.wordpress.org/plugins/classic-widgets/). This plugin, once activated, and when you use a classic (non-block) theme, restores the previous widget settings screens and disables the block editor for widget management. There are no other settings, the classic widget settings screens are enabled or disabled by enabling or disabling this plugin. Classic Widgets is an official plugin maintained by the WordPress team that restores the previous ("classic") WordPress widget screens. You will receive support and maintenance until at least 2024 or as long as needed.

Then, we went to “Go to site folder”, from the main panel of the Local app, and we went to “app > public”, the folder where the WordPress installation is located on our computer.
Then we enter the “wp-content > themes” folder to reach the content of the “twentytwentyone” directory. There the functions.php file was opened and we pasted in the code to create the new after entry widget area:
 
> register_sidebar( array(
	'id' = 'after-entry',
	'name' = __( 'After entry', ' <textdomain' ),
	'description' = __( 'This widget area appears only after content on individual posts page', '<textdomain' ),
	'before_widget' = '<div id=" %1$s" class="widget-container %2$s"',
    'after_widget' = '</div',
) );
 
(Don't forget to replace <textdomain> with your own domain text.)

With the definition inside functions.php done, the next step was to include the function call inside the file with the individual file programming. In the case of the Twenty-Twenty One theme, you need to edit the "template-parts > content > content-single" file and add the following just after the "the_content();" statement. [remember to add a semicolon after the_content()]
 
> if ( is_active_sidebar( 'after-entry' ) ) {
  dynamic_sidebar( 'after-entry' );
}
 
## Conclusions
  
You've learned how to create a new widget area to your classic theme (if the theme developer didn't set it up).


We have included the automated theoretical explanation of ChatGPT in order to experience the experience of this artificial intelligence or machine learning tool.
I await your comments.
