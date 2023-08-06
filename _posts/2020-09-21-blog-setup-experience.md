---
title: Setting Up the Blog
layout: post
---

The creation of this blog was mostly just a matter of following the instructions provided by GitHub, but I did run into a few issues that I wanted to highlight in this blog post.

The main documentation for GitHub Pages is located here:
* [Working with GitHub Pages](https://docs.github.com/en/github/working-with-github-pages)

GitHub Pages uses Jekyll as its static site generator, so I spent a lot of time with these two pages:
* [Creating a GitHub Pages site with Jekyll](https://docs.github.com/en/github/working-with-github-pages/creating-a-github-pages-site-with-jekyll).
* [Testing your GitHub Pages site locally with Jekyll](https://docs.github.com/en/github/working-with-github-pages/testing-your-github-pages-site-locally-with-jekyll)

Following these instructions, the first issue occurred when I tried to generate the Jykell skeleton:

```bash
$ bundle exec jekyll 3.9.0 new .
Could not locate Gemfile or .bundle/ directory
```

I am not a Ruby programmer and have no experience with the Ruby egosystem, so the `bundle` command was totally unfamiliar to me. The `3.9.0` in the `bundle` command comes from the [Dependency versions](https://pages.github.com/versions/) which I believe indicates that GitHub Pages is compatible with Jekyll 3.9.0. Reading the documentation, and Google searching did not really provide a solution. So I thought maybe Jekyll was not installed correctly. However my initial attempts to install Jekyll were unsuccessfull:

```bash
$ jekyll 3.9.0 new .
fatal: 'jekyll 3.9.0' could not be found. You may need to install the jekyll-3.9.0 gem or a related gem to be able to use this subcommand. 
```

```bash
$ gem install jekyll-3.9.0
ERROR:  Could not find a valid gem 'jekyll-3.9.0' (>= 0) in any repository
```

Finally this command worked:

```bash
$ sudo gem install jekyll 3.9.0
Successfully installed jekyll-4.1.1
Parsing documentation for jekyll-4.1.1
Done installing documentation for jekyll after 1 seconds
ERROR:  Could not find a valid gem '3.9.0' (>= 0) in any repository
1 gem installed
```

But as the output showed, it installed version `4.1.1` instead of `3.9.0`. The space between the gem (jekyll) and the version was a mistake. Gem interpreted it as a request for two separate Ruby gems which is why it generated the error. Rather than mess around with trying to get the correct version, I went ahead with version `4.1.1`. 

After getting Jekyll installed I was able to create the Jekyll skeleton using the `new` command:

```bash
$ jekyll new . --force
Running bundle install in /Users/dan/workspaces/blog/dmmx.github.io... 
```

With that I was able to create posts and push them up to GitHub with the usual `add` -> `commit` -> `push` workflow. The next step was to run Jekyll locally so I could test the blog posts before pushing them up to GitHub. To do that I tried the `jekyll serve` command but received an error:

```bash
jekyll serve
...
Could not find gem 'github-pages' in any of the gem sources listed in your Gemfile. (Bundler::GemNotFound)
```

so I installed github-pages:

```bash
$ gem install github-pages
```

Next invocation of `jekyll serve` also errored:

```bash
$ jekyll serve
...
Unable to satisfy the following requirements: (Bundler::Molinillo::VersionConflict)
```

After a few more attempts and a few more errors, I went back to using bundle:

```bash
$ bundle exec jekyll serve
```

And that worked! I could now view my blog on port 4000 on my local machine.


