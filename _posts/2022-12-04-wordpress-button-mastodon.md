---
published: false
layout: post
title: How to add a Mastodon share button to your WordPress
author: Antonio C.
categories: wordpress
---
In this post we will see the different ways that exist to add a Mastodon share button to each of your blog posts. With that button, your blog readers will be able to post a toot in their Mastodon instance, related to any of your posts.

About Mastodon and the integration between this decentralized network and WordPress, I suggest [How to integrate WordPress and Mastodon](https://www.blogpocket.com/2022/11/29/como-integrar-wordpress-y-mastodon/).

##Creating a Mastodon share button: GitHub

Before we see how to create a Mastodon share button within a WordPress blog, let's see how to do it on GitHub and Jekyll.

I decided to reborn [my blog on Github](https://blogpocket.github.io/), dedicating it to publishing English versions of my posts on Blogpocket.com.

To find out how to create a blog on Github, I invite you to read [How to have a blog with GitHub and Jekyll](https://www.blogpocket.com/2018/09/02/tener-un-blog-con-github-y-jekyll/).

Customizing a GitHub and Jekyll blog requires some technical knowledge, especially HTML and CSS.
Add the following code to the /_layouts/post.html file:

> <a title="Share on Mastodon" href="https://tootpick.org/#text=Check%20out%20https://myblogen.github.io{{ page.url }}%20by%20@user@instance.mastodon"<img src="https://edent.github.io/SuperTinyIcons/images/svg/mastodon.svg" width="40" alt="mastodon icon" /</a

The "trick" to get that HTML code to work is based on the following:

- Using [Juerd Waalboer](https://github.com/Juerd) 's [Toopick](https://github.com/Juerd/tootpick) software, to display the screen that allows you to customize the toot text and choose the instance. Unlike a share button in a centralized network, you need to know the url of the specific instance to which you want to send the message. Thanks to Terence Eden, I found out about this software in a comment to the [Create a «Share To Mastodon» Button for WordPress](https://shkspr.mobi/blog/2022/06/create-a-share-to-mastodon-button-for-wordpress/). Toopick's software, like [Toot Proxy](https://toot.kytta.dev/)'s [Nikita Karamov](https://www.kytta.dev/), can also be self-hosted, but it's more accessible than with the other because Tootpick is built as a single static HTML file. It's also more privacy-friendly, as explained in the project's documentation. It is recommended that the software runs from your own server so as not to depend on external resources, which implies dependency and low final loading speed. Check the Blogpocket archive to learn how to self-host this software (post in preparation).
- The icon image, corresponding to Mastodon, can be uploaded to a folder in your GitHub installation (images). But you can also use edent.github.io/SuperTinyIcons/images/svg/mastodon.svg. Although it is more advisable, to host the file with the icon on your server, for the same reason described for the software.

The text that appears in the box by default, as well as the size of the icon, can be customized within the above code. As shown in the snippet below, you can put your own GitHub domain immediately before {{ page.url }}.

> myblog.github.io{{ page.url }}

And you can also change your Mastodon user to:

> %20by%20@user@instance.mastodon

Icon size is changed to:

> width="40"

###More Sharing projects on Mastodon

As you can read in the Toopick documentation, this is not the first of its kind. It is inspired by:

- [toot](https://codeberg.org/kytta/toot)
- [Advanced Sharer for Mastodon](https://sharetomastodon.github.io/about/)
- [Mastodon Share Button](https://aly-ve.github.io/Mastodon-share-button/)

 
##Creating a share button in Mastodon: WordPress without a plugin

From the implementation of the share button in Mastodon came the idea of doing it in WordPress without using any special social sharing plugin.

Let's see some ideas to carry it out in:

A classic theme.
A block theme.

###Classic theme 

In a classic WordPress theme, we have the widget areas to customize the website.

If the theme developer has prepared an “after entry” widget area, we can use this to add the widget available when we install and activate the [Insert PHP Code Snippet plugin](https://wordpress.org/plugins/insert-php-code-snippet/). This plugin allows you to create PHP code snippets and associate them with a short code. In addition, it includes a widget to use in the widget areas.

In this case, we will create a new snippet and add the “Custom PHP Code” widget to the After Entry widget area. In the widget configuration, we will choose the name of the snippet from the drop-down.

With that, we have all the gear to prepare a PHP code, based on the HTML code that we saw in the previous GitHub section. The snippet would be:

> <?php
global $wp;
$current_slug = add_query_arg( array(), $wp-request );
echo '<a title="Share on Mastodon" href="https://tootpick.org/#text=I suggest you:%20https://www.miblog.com/'.$current_slug.'%20by%20@ usert@myinstance.mastodon"<img src="https://edent.github.io/SuperTinyIcons/images/svg/mastodon.svg" width="80" alt="Mastodon Icon" /</a ';
?
 
Notice that before displaying the image, the slug corresponding to the post is obtained:

> global $wp;
$current_slug = add_query_arg( array(), $wp-request );

And then the echo statement is used to display the same literal (HTML) that we used in the GitHub section.

To learn about the different options when it comes to obtaining the current URL, I recommend the masterwp article: [How to Get Current URL in WordPress (PHP Snippet)](https://smartwp.com/wordpress-get-current-url/).

If there was no after entry widget area, it would have to be created. That is beyond the purpose of this article, so I refer you to the Blogpocket archive (post in preparation).

###Block theme

In a block theme there is no widget area, but we have the template in the site edition.
Simply, you have to edit the template corresponding to the individual post and add a shortcode block at the end, in which we will incorporate the one corresponding to the same snippet that we saw in the Classic theme subsection.

##Creating a Mastodon share button: WordPress with plugin

Terence Eden mentions in his article that the Jetpack plugin (supposed to be the Jetpack Social plugin) allows you to add the Mastodon icon and configure it but I couldn't get it to work.
There are other social sharing plugins. Most do not contemplate Mastodon.

Among those who contemplate decentralized networks like Mastodon, there is the [AddToAny Share Buttons](https://es.wordpress.org/plugins/add-to-any/) but I couldn't get it to work either.

Logically, this section is left open, although we should pursue a self-hosted solution and avoid plugins.

But, whether you have a classic theme, with an After Entry widget area, or a block theme, using the Insert PHP Code Snippet and Toopick plugin seems like the best option.

##Conclusions

The problem with implementing a share button on a decentralized platform, like Mastodon, is that a variable with an unknown value is needed, which is the instance.

We have seen different alternatives but it seems that implementing simple software on your server, in the style of Toopick, is the best solution. Let's not forget that we strive to maintain the high level of performance optimization and preserve privacy.

Both in the [Blogpocket blog](https://www.blogpocket.com/), as in [eCuaderno](https://www.ecuaderno.com/) (José Luis Orihuela) and [blogpocket.github.io](https://blogpocket.github.io/) you can see the Mastodon share button working, using the Toopick software.
