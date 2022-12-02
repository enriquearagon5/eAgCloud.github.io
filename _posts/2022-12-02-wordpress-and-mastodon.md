---
published: true
layout: post
image: null
author: Antonio C.
categories: wordpress
---
## How to integrate WordPress and Mastodon

In this post I give you the keys to integrate WordPress with Mastodon. And, at the end, you will find the special episode of MADE WITH BLOCKS (in spanish), in which I give you the keys to said integration.

This post was first published (in Spanish) on Blogpcket.com.

- How to create a bot in a Mastodon instance, using a WordPress plugin.
- How to verify pages of a WordPress website for your Mastodon profile.
- How to turn a WordPress website into a kind of Mastodon instance.
- How to get the Mastodon social icon using a WordPress block.

## **How to create a bot in a Mastodon instance, using a WordPress plugin**


We Will start WordPress integration with Mastodon, learning how to create a bot in a Mastodon instance.

For example, I have created a bot with Blogpocket.com updates (posts and podcast episodes) in the Wptoots.social instance. To do this, I created the account [@hechoconbloques@wptoots.social](https://wptoots.social/@hechoconbloques), and in its configuration, I chose the option “This is a bot account”, within the profile.

To send Blogpocket.com posts automatically to that Mastodon account, I simply installed the [Mastodon Autopost](https://es.wordpress.org/plugins/autopost-to-mastodon/). To get it up and running, all you have to do is adjust your credentials and posting preferences in “Settings > Mastodon Autopost”.

## **How to Verify WordPress Website Pages for Your Mastodon Profile**

In Mastodon, the first thing you need to fill out is your profile. This allows you to add up to four links and if you want to verify any of them, you simply have to add to those pages an HTML code that you can capture from the same profile.

But verification can only be done if you are the owner of those pages.

You can do it manually, if you are able to access the HTML code (with the WordPress site editor that is very easy) or through a plugin.

The plugin that I have used to verify the pages and posts of Blogpocket.com is [Simple Mastodon Verification](https://wordpress.org/plugins/simple-mastodon-verification/). This plugin provides a General Settings menu option to define a rel=”me” in meta tags for the entire site.

As of version 1.1, this plugin also offers the option to verify individual authors, providing publishers with an easy method to verify author Mastodon profiles. The latter allowed, in my case, to also automatically verify the link to the author page that acts as a Mastodon instance (see section «How to convert a WordPress website into a kind of Mastodon instance»).

## **How to convert a WordPress website into a kind of Mastodon instance**

You can read the process corresponding to this section in [Your WordPress blog as an instance of Mastodon (fediverse)](https://www.blogpocket.com/2022/11/22/tu-blog-de-wordpress-como-una-instancia-de-mastodon-fediverso/).

But basically, it consists of installing, activating and configuring [ActivityPub](https://es.wordpress.org/plugins/activitypub/) Matthias Pfefferle’s. The plugin implements the ActivityPub protocol for your website. Your readers will be able to follow blog posts on Mastodon and other federated platforms supported by ActivityPub.

In my case, I implemented the [@acambronero@www.blogpocket.com](https://www.blogpocket.com/author/antonio) so that the posts and podcast episodes can be followed.

I also installed the [WebFinger](https://es.wordpress.org/plugins/webfinger/) and [NodeInfo(2)](https://es.wordpress.org/plugins/nodeinfo/) because according to the ActivityPub plugin documentation it can help make everything work better. Let’s not forget that the ActivityPub plugin is in beta version.

## **How to Get the Mastodon Social Icon Using a WordPress Block**

Finally, getting the Mastodon social icon can be very useful and that is very easy with the native WordPress Social Icons block. Simply insert it and you can add that icon to your design.

## **See it In action**

In [this video](https://vimeo.com/blogpocket/hcb20) (in spanish) you can see how we have implemented the four previous sections in Blogpocket.com; that is, how we have integrated our WordPress and Mastodon.

Practice your Spanish ;)
