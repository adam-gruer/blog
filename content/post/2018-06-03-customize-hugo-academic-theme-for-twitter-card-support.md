---
title: customize hugo-academic theme for twitter card support
author: Adam Gruer
date: '2018-06-03'
slug: customize-hugo-academic-theme-for-twitter-card-support
draft: true
categories:
  - Tips
tags:
  - hugo
  - hugo-academic
  - templates
  - twitter-card
header:
  caption: ''
  image: ''
---
:tada:

A quick tip to add better twitter card support if you are using the Hugo-[Academic theme](https://sourcethemes.com/academic/) thanks to [George Cushen](https://twitter.com/georgecushen).
Thanks to [this post from Village Blacksmith Consulting](http://villageblacksmith.consulting/hugo-twitter-cards/) for finally helping the puzzle.
[and this post](https://xvrdm.github.io/2017/10/23/socialize-your-blogdown/?utm_content=buffere1410&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)

What's a twitter card?  When you share a link to your new blog post, if the post has the required meta data the link will appear as richer display will appear

```bash
~/blog/
└── themes
    └── hugo-academic
        └── layouts
            └── partials
                └── header.html
```

```html
  <meta property="twitter:card" content="summary_large_image">
  {{ range where $.Site.Params.social ".icon" "twitter" }}
  <meta property="twitter:site" content="@{{ replaceRE "^//twitter.com/([^/]+)" "$1" .link }}">
  <meta property="twitter:creator" content="@{{ replaceRE "^//twitter.com/([^/]+)" "$1" .link  }}">
  {{ end }}
  {{ if .IsPage }}
<meta name="twitter:description" content="{{ .Summary }}" />
<meta name="twitter:title" content="{{ .Title }}" />
<meta name="twitter:image" content="{{ .Params.image }}" /> 
{{ else }}
<meta name="twitter:title" content="{{ .Site.Title }}" />
<meta name="twitter:description" content="{{ .Description }}" />
{{ end }}
```
