Title: creating a blog with pelican and github io pages
Date: 2016-11-24 18:52
Modified: 2019-11-02 19:30
Category: development 
Tags: blog, pelican, python, github 
Author: Vitor Carvalho 
Slug: creating-a-blog-with-pelican-and-github-io-pages
Summary: So I decided to create a blog and write about my learning process in a feel areas.  My first post will be how I end up with a blog with [Pelican](http://getpelican.com/){:target="_blank"} - a static site generator - that was written in Python language.


So I decided to create a blog and write about my learning process in a feel areas.
My first post will be how I end up with a blog with [Pelican](http://getpelican.com/){:target="_blank"}
- a static site generator - that was written in Python language.


My skills in development are mainly in Python, so I look up for a tool that help me
to maintain a blog and the search ends with this Pelican tool. I started to read the 
manual (RTFM!) and to begin you will need Python version 2.7.x or 3.3+. Here I'm using poetry
to help me keep my environment clean.

```shell
$ mkdir ~/blog && cd ~/blog
$ poetry init # you will have to answer some questions choose no when asked to define dependencies
$ poetry shell
$ poetry add pelican Markdown 
$ pelican-quickstart 
```

You will have to answer several questions about your blog after the `pelican-quickstart`
command. Answer **Yes** when asked to upload your blog using GitHub Pages.
Then, you can run the development server delivered with Pelican. 

```shell
$ pelican -rl 
```

Done! Now you have a blog to work with. Your articles and posts will be saved in
`content` directory. You can create a file:

```shell
$ touch content/simple-article.md
```

Let's see a content sample blog post `simple-article.md`:

```markdown
Title: Nice simple article title 
Date: 2016-11-24 10:00

Write some important content here. 
```

Since you have ran the development server (with auto-reload option enabled), the file will be 
automatically refreshed and you can access [localhost:8000](http://localhost:8000){:target="_blank"}. 
Very nice.

### Publishing your site

Now let's publish this blog within [Github Pages](https://pages.github.com/){:target="_blank"}.
Create a new repository named `username.github.io` and run the following commands:

```shell
$ poetry add ghp-import
$ git init
$ git remote add origin <url-repository>
$ git checkout -b blog 
$ echo 'output' >> .gitignore
$ git add .
$ git commit -m "first commit"
$ git push origin blog
```

Now we have all the blog structure at github. Let's use `ghp-import` to publish the blog.

    :::shell
    make github

Your blog is accessible by the link username.github.io. That is it.

Things you can do by yourself

* Change the default theme, using one of the listed in 
[Pelican Themes](http://www.pelicanthemes.com/){:target="_blank"}.
* Edit the selected theme to your needs.
* Add some plugins to your blog. Read 
[Pelican Plugins](https://github.com/getpelican/pelican-plugins){:target="_blank"}.

