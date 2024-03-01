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

In `base.html`, add the following:
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="utf-8">
    <title>CIF Example Site</title>
</head>

<body>
    <section class="section">
        <div class="container">
            {% block content %} {% endblock %}
        </div>
    </section>
</body>

</html>
```

In `index.html`, add the following:
```html
{% extends "base.html" %}

{% block content %}
<h1 class="title">
  CIF Example Website
</h1>
{% endblock content %}
```

Now, run `zola serve`, and click the link it gives you (http://127.0.0.1:1111/). You should see your rendered `index.html` displaying your website title.

Now, let's make our first blog viewable.

Add the following to `page.html`:
```html
{% extends "base.html" %}

{% block content %}
<h1 class="title">
    {{ page.title }}
</h1>
<p class="subtitle"><strong>{{ page.date }}</strong></p>
{{ page.content | safe }}
{% endblock content %}
```

Make sure `zola serve` is running, and go to http://127.0.0.1:1111/blog/first-blog/. You should see your blog post!

Now, let's make sure we can navigate to our blog posts without having to manually enter the link. 

In `_index.md`, add the following:

```md
+++
title = "Blog Posts"
sort_by = "date"
template = "blog.html"
page_template = "page.html"
+++
```

Make sure `zola serve` is running, and go to http://127.0.0.1:1111/blog/. You should see the proper title and a clickable list of your blog posts (which for right now is just one).

Now, let's make it so we can get to the blog post page from the homepage (`index.html`). 

Add this line before the `{% endblock content %}`:

```html
<p>Click <a href="{{ get_url(path='@/blog/_index.md') }}">here</a> to see my posts.</p>
```

Go to http://127.0.0.1:1111/, and now you can navigate your entire website from the homepage.

Congratulations! You now have a functioning blog post website!

### Next Steps

Your website at this point won't look very pretty. It's base html, after all. You will want some CSS and HTML formatting.

To get a taste of this, try out [simple.css](https://raw.githubusercontent.com/kevquirk/simple.css/main/simple.css) (right click -> Save Page as... -> save to a new folder `css` in the `static` folder). 

Now, in your `base.html`, add the following line in the `<head>` section:

```html
<link rel="stylesheet" href="/css/simple.css">
```

Now make sure `zola serve` is running and reload your pages. Your site should look considerably better!

### Upload to Github

After getting Github Student, you have access to Github Pro! This gives you free static website hosting at `<yourgithubusername>.github.io`. 

After getting Github Pro, you can make a new repository on your account that is called `<yourgithubusername>.github.io`. For help with this see [github pages documentation](https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site).

Then, in your zola directory, do `zola build`. this will create a folder called `public`. This is your fully rendered static website. Upload the files in `public` to your `<yourgithubusername>.github.io` repository and within a few minutes, your website should be live at `<yourgithubusername>.github.io`. 

### That's All!
For assistance with any details outlined here, join the [CIF discord](https://discord.gg/TMKXqJc) and use the `#ask-cif` channel to ask any questions you may have. 
