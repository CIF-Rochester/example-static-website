# example-static-website
Example static webiste for 2/29/2024 Tech Seminar on building websites.

### Installing Zola
- https://github.com/getzola/zola/releases
- https://www.getzola.org/documentation/getting-started/installation/

### Zola Setup
- `zola init`
- enter: `https://<yourgithubusername>.github.io`
- `> Do you want to enable Sass compilation? [Y/n]: n`
- `> Do you want to enable syntax highlighting? [y/N]: y`
- `> Do you want to build a search index of the content? [y/N]: n`

#### Create the following empty files:
- `base.html`, `page.html`, `blog.html`, `index.html` in the `templates` folder
- create a `blog` folder inside the `content` fodler
- `_index.md` in `blog` folder

Your folder structure should now look like this:
```
├── config.toml
├── content/
│   └── blog/
│  	 └── _index.md
├── static/
├── templates/
│   ├── base.html
│   ├── page.html
│   ├── blog.html
│   └── index.html
└── themes/
```

### Add Content

Create a file called `first-blog.md` in `content/blog`.
Add the following text to the file:
```md
+++
title = "First Blog"
date = 2024-2-29
+++

# First Blog
Content of the first blog.
```


