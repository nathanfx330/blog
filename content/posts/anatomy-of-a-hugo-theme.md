+++
date = '2025-09-01T02:56:51-04:00'
draft = false
title = 'Anatomy of a Hugo Theme'
+++

My recent journey into building a Hugo blog led me down a rabbit hole of complex themes.  
https://gohugo.io/

While powerful, they often felt like a black box. I decided to strip everything away and ask: what are the absolute essentials to make a Hugo theme work?

To truly start from "scratch," you first need the underlying folder structure. There is a blank slate theme that nobody talks about called **Zen**. It’s a bare-minimum boilerplate that sets up the necessary folders and semantic HTML without any of the bloated CSS or scripts.

First, you need to download this theme into your project. Open your terminal at the root of your Hugo site and run this command to clone it directly from its repository https://github.com/frjo/hugo-theme-zen :

```bash
git clone https://github.com/frjo/hugo-theme-zen.git themes/zen
```

Once Zen sets up your folders, you can strip it right down to the absolute bare minimum to see how it ticks. It turns out, you really only need three core files.

### 1. The Skeleton: `layouts/_default/baseof.html`

This is the master template for the entire site. It's the HTML document that holds everything else. The most important part is the `{{ block "main" . }}` section, which acts as a hollowed-out space where other templates will inject their content.

```html
<!DOCTYPE html>
<html>
<head>
    <title>{{ .Title }}</title>
</head>
<body>
    <main>
        {{ block "main" . }}{{ end }}
    </main>
</body>
</html>
```

### 2. The Homepage: `layouts/index.html`

This template defines what goes into the "main" block on your homepage. Its job is typically to loop through all your pages and create a list. The `{{ range .Site.RegularPages }}` function is the engine for this.

```html
{{ define "main" }}
    <h2>Posts</h2>
    <ul>
        {{ range .Site.RegularPages }}
            <li><a href="{{ .Permalink }}">{{ .Title }}</a></li>
        {{ end }}
    </ul>
{{ end }}
```

### 3. The Content Page: `layouts/_default/single.html`

Finally, this template defines how to display a single piece of content, like this very blog post. It pulls in the specific post's title (`{{ .Title }}`) and its main content (`{{ .Content }}`).

```html
{{ define "main" }}
    <article>
        <h2>{{ .Title }}</h2>
        <div>
            {{ .Content }}
        </div>
    </article>
{{ end }}
```

And that's it. With just these three files, you have a complete, functional theme. It's a powerful and minimalist foundation to build upon.

Feel free to use this as a starting point. Happy writing!