# Search Engine Optimisation (SEO)

*The following is a run down of best practices to use to ensure we deliver projects that are naturally optimised for search engine visibility. If we build with this in mind, we don't have retrofit our work later with it. That said, it is NOT set in stone. If you have any questions, improvements, suggestions, do speak up and hopefully we can improve it.*

## Table of Contents

1. [Title And Description](#title-and-description)
1. [Canonical Links](#canonical-links)
1. [URL Structure](#url-structure)
1. [Duplicate Content](#duplicate-content)
1. [Header Tags](#header-tags)
1. [Images](#images)
1. [Pagination](#pagination)
1. [Sitemap](#sitemap)
1. [Authorship Tags](#authorship-tags)
1. [Microdata](#microdata)

## Title and Description

These title and description tags will often form the basis of the search result listings, so should also be created to entice users to click the result.

* Every page needs a unique title and description.
* All must be completely unique, with no duplicates.
* Should be keyword rich.

## Canonical Links

A canonical page is the preferred version of a set of pages with highly similar content.

* Every page will need a canonical link tag adding.
* Canonical link tags are case specific.  

```
<link rel="canonical" href="http://www.example.com/example-page" />
```

## URL Structure

* Needs to be kept simple for easy sharing.
* Use of keywords within the URL structure.

## Duplicate Content

* Ensure no duplicate pages are created on the site.
* Ways of dealing with duplicate content
    * 301 redirect into main page
    * Canonical link tag
    * Add noindex tag
* Special pages for PPC should usually be noindex.

## Header Tags

* Use Header tags appropriately. Lookup semantics, and you'll get a good idea of what and what not to use, where and when. Eg. h1, h2, h3, accordingly.

## Images

* Images should be included in the page and not in the CSS where possible, to allow google to index them.
* If you can't decide whether to put an image inline or in CSS, disable printing background images and go to print a page and see if the image will print. Things like logos, body content images should be visible.
* This goes without saying, file sizes should be kept to a minimum to optimise download speed.
* Keep your Alt text and Image titles unique per each image.
* Use no more than 7 words for Alt text.
* Avoid keyword stuffing.
* Make your images informative and detailed with important keywords.
* Get good-quality images with a specified width and height for each one.
* Google ranks sites for mobile, images need to be mobile compatible.

## Pagination

* On pages that are sequential, such as blogs we need to add pagination code.

```
<link rel="prev" href="http://www.example.com/blog/page/1" />
<link rel="next" href="http://www.example.com/blog/page/2" />
```

## Sitemap

* Every site needs a sitemap page adding.
* This should be linked to from every page.
* .Only needs to include key pages / sections.

## Authorship Tags

* Article Page
```
<a rel="author" href="/advice/authors/Joe-Bloggs/">Joe Bloggs</a>
```
* Bio Page
```
<a rel="me" href="https://plus.google.com/117509091157300032892/">Joe Bloggs</a>
```

## Microdata

Microdata is a way to label specific content on a website for example reviews, personal information, telephone numbers, Company Address etc.

Micro data is often contained within a div or a span tag, e.g
```
My name is <span itemprop="name">Bob Smith</span>
```

There is a number of micro data tags that we could use across the different domains, we should try and keep them standardized and included in any future projects.
