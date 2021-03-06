# DEPRECATED: grunt-blog

```
****************************************************************************************
* WARNING: DEPRECATD                                                                   *
* We wanted Jekyll without a build procedure for every modification                    *
* In other words, we wanted live merging between markdown and html tenmplates          *
* We hoped to be able to achieve that with a client-side SPA architecture              *
* but search engine bots are poor at crawling dynamic content                          *
* Good SEO requires a server-side architecture                                         *
* Memba Blog Engine v0.0.1 can still be used with grunt-blog but do not expect         *
* the generated blog to be indexed by search engines                                   *
* Newer releases of Memba Blog Engine do not make use of grunt-blog                    *
****************************************************************************************
```

> A grunt plugin to organize markdown content and generate indexes for [Memba Blog Engine](https://github.com/Memba/Memba-Blog).

[![NPM](https://nodei.co/npm/grunt-blog.png?downloads=true&stars=true)](https://npmjs.org/package/grunt-blog)

## Overview

This plugin works as a component of [Memba Blog Engine](https://github.com/Memba/Memba-Blog). It performs 3 tasks:

1. Analysing and updating the markdown in all the md files located in the *news* directory,
2. Copying the new updated files in a chronological hierarchy under the *posts* directory,
3. Indexing these files in the form of an RSS file at the root of the *posts* directory.

## Getting Started
This plugin requires Grunt `~0.4.2`

If you haven't used [Grunt](http://gruntjs.com/) before, be sure to check out the [Getting Started](http://gruntjs.com/getting-started) guide, as it explains how to create a [Gruntfile](http://gruntjs.com/sample-gruntfile) as well as install and use Grunt plugins. Once you're familiar with that process, you may install this plugin with this command:

```shell
npm install grunt-blog --save-dev
```

Once the plugin has been installed, it may be enabled inside your project's Gruntfile with this line of JavaScript:

```js
grunt.loadNpmTasks('grunt-blog');
```

and configured by adding a section named `blog` to the data object passed into `grunt.initConfig()`.

```js
grunt.initConfig({
  blog: {
    options: {
      //
      //Web site options
      home: '...',
      route: '...',
      index: '...',
      sitemap: '...',
      //
      //File options
      homeRoot: '...'
      newsRoot: '...',
      postsRoot: '...',
      //
      //RSS options
      category: '...',
      copyright: '...',
      description: '...',
      docs: '...',
      generator: '...',
      image: '...',
      language: '...',
      lastBuildDate: '...',
      link: '...',
      managingEditor: '...',
      pubDate: '...',
      rating: '...',
      title: '...',
      ttl: '...',
      webMaster: '...'
    },
    your_target: {
      // Target-specific options go here.
    },
  },
});
```

## The "blog" task configuration

### Web site options

#### options.home
Type: `String`
Default value: `'http://miniblog.memba.com'`

The home of your blog where index.html can be reached.

#### options.route
Type: `String`
Default value: `'#/blog/'`

The SPA route to blog posts, e.g.: `'http://miniblog.memba.com#/blog/2013/11/vision-for-a-new-blog-engine'`

#### options.query
Type: `String`
Default value: `'?r='`

The replacement for '#' to access blog posts via query strings, e.g.: `'http://miniblog.memba.com?r=/blog/2013/11/vision-for-a-new-blog-engine'`

#### options.index
Type: `String`
Default value: `'index.rss'`

The file name of the RSS index located in options.postsRoot. Unless you dig into the code of Memba Mini Blog Engine, we recommend keeping the default value.

#### options.sitemap
Type: `String`
Default value: `'sitemap.xml'`

The file name of the XML sitemap located in options.homeRoot. Unless you dig into the code of Memba Mini Blog Engine, we recommend keeping the default value.

### File options

#### options.homeRoot
Type: `String`
Default value: `''`

Location of index.html.

This is the portion of options.newsRoot and options.postsRoot that we should remove to build relative paths to display media files.

#### options.newsRoot
Type: `String`
Default value: `'news'`

The directory containing the new md files which should be added as posts to the blog.

An md file is a text file with:

1. the *.md extension,
2. meta data in the form key:value\n at the top
2. [markdown] (http://daringfireball.net/projects/markdown/) at the bottom separated from the meta data by \n\n

*Note: \n is a line feed*

For example:

```shell
title: my title
description: my description

Some markdown here
```

#### options.postsRoot
Type: `String`
Default value: `'posts'`

The directory of published md files and media files organized chronologically by grunt-blog.

### RSS Options

For more information:

See http://cyber.law.harvard.edu/rss/rss.html
See http://www.w3schools.com/rss/rss_channel.asp.

#### options.category
Type: `String`
Default value: `'Web Development'`

The category the RSS channel belongs to. Also used as a default category for items.

See http://www.w3schools.com/rss/rss_tag_category_channel.asp
See http://www.w3schools.com/rss/rss_tag_category_item.asp

*Note: There can only be one category at this stage.*

#### options.copyright
Type: `String`
Default value: `'Copyright (c) 2013-2014 Memba. All rights reserved.'`

Notice of copyrighted material.

See http://www.w3schools.com/rss/rss_tag_copyright.asp

#### options.description
Type: `String`
Default value: `'A static blog engine which displays live markdown content (What You Write Is What You Publish).'`

A description for the channel, used as a default description for items.

See http://www.w3schools.com/rss/rss_tag_title_link_description_channel.asp
See http://www.w3schools.com/rss/rss_tag_title_link_description_item.asp

#### options.docs
Type: `String`
Default value: `'http://cyber.law.harvard.edu/rss/'`

URL to the documentation of the format used in the RSS feed.

See http://www.w3schools.com/rss/rss_tag_docs.asp

#### options.generator
Type: `String`
Default value: `'http://miniblog.memba.com'`

Program used to generate the RSS feed.

See http://www.w3schools.com/rss/rss_tag_generator.asp

#### options.image
Type: `String`
Default value: `'http://miniblog.memba.com/styles/images/logo.png'`

Image to display when aggregators present a feed.

See http://www.w3schools.com/rss/rss_tag_image.asp

#### options.language
Type: `String`
Default value: `'en-US'`

The language the channel is written in.

See http://www.w3schools.com/rss/rss_tag_language.asp

#### options.lastBuildDate
Type: `Date`
Default value: `new Date().toISOString()`

Last modified-date for the content in the RSS feed.

See http://www.w3schools.com/rss/rss_tag_lastbuilddate.asp

#### options.link
Type: `String`
Default value: `'http://miniblog.memba.com/posts/index.rss'`

A link to the channel.

See http://www.w3schools.com/rss/rss_tag_title_link_description_channel.asp
See http://www.w3schools.com/rss/rss_tag_title_link_description_item.asp

#### options.managingEditor
Type: `String`
Default value: `'Memba'`

E-mail address for the editor of the content of the feed, also used as default for item authors.

http://www.w3schools.com/rss/rss_tag_managingeditor.asp

#### options.pubDate
Type: `Date`
Default value: `new Date().toISOString()`

Last publication date for the content in the RSS feed.

See: http://www.w3schools.com/rss/rss_tag_pubdate.asp

#### options.rating
Type: `String`
Default value: `undefined`

The PICS rating of the feed.

See: http://www.tutorialspoint.com/rss/pics-ratings.htm

#### options.title
Type: `String`
Default value: `'Memba Mini Blog Engine'`

A title for the channel.

See http://www.w3schools.com/rss/rss_tag_title_link_description_channel.asp
See http://www.w3schools.com/rss/rss_tag_title_link_description_item.asp

#### options.ttl
Type: `Number`
Default value: `1440`

The <ttl> (ttl=time to live) element specifies the number of minutes the feed can stay cached before refreshing it from the source.

See http://www.w3schools.com/rss/rss_tag_ttl.asp

#### options.webMaster
Type: `String`
Default value: `'Memba'`

E-mail address to the webmaster of the feed.

See http://www.w3schools.com/rss/rss_tag_webmaster.asp

### Usage Example

In this example, we show you the typical configuration you should be considering in your project.

```js
grunt.initConfig({
  blog: {
    options: {
          home: 'http://yoursite/index.html', //The path to your Mini Blog Engine
          newsRoot: 'news', //your news directory
          postsRoot: 'posts', //your posts directory
          title: 'Your title for your RSS channel',
          link: 'http://yoursite',
          description: 'Your description for your RSS channel',
          copyright: 'Copyright (c) 2013-2014 You. All rights reserved.',
          category: 'Web Development', //The default category for your blog posts
          managingEditor: 'The default author for your blog posts',
    }
  },
});
```

## Contributing
In lieu of a formal style guide, take care to maintain the existing coding style. Add unit tests for any new or changed functionality. Lint and test your code using [Grunt](http://gruntjs.com/).

## Release History
- _v0.1.5_ Readme and image processing (enclosures)
- _v0.1.6_ Sitemap generation and test of hashbangs
- _v0.1.7_ Another SEO Test: combination of hash routes and query string sitemap
