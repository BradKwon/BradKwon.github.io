Brad Kwon's blog site

Originated by #Clean Blog by Start Bootstrap - Jekyll Version

## Development setup

#### 1. Install Jekyll
Please follow this guide from Jekyll official site.
https://jekyllrb.com/docs/installation/

#### 2. Run bundle
Run `bundle` in your terminal.

````bash
> bundle
````

#### 3. Run this blog site in localhost

````bash
> bundle exec jekyll serve --watch
````

If you just want to build it,

````bash
> bundle exec jekyll build
````

#### 4. Sitemap update

1. Generate sitemap with any of online tools mentioned in this article.
[SitemapGenerators.wiki](https://code.google.com/archive/p/sitemap-generators/wikis/SitemapGenerators.wiki)
At the moment, I'm using this online tool. [xmlsitemapgenerator](https://xmlsitemapgenerator.org/)

2. Update `sitemap.xml` in this project and push to the repository.

3. When the new sitemap is published by GitHub Action, go to Google search console and submit the new `sitemap.xml`
