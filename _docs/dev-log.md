---
title: Dev log
---

<hr>

# buildings page
<br><br>

## buildings.html
imports the layout


## _layouts/buildings.html
`buildings.html` is where architectural categories are rendered in a tile (card pop-up) form.

## _data/settings.yml

In `settings.yml`, you define architectural categories within the field `buildings:`


``` ruby
# setting.yml

buildings: 
  filters:
    - name: "All"
      slug: "box-item"
      active: 1

    - name: "Art Nouveau"
      slug: "f-nouveau"
      active: 0

    - name: "Louis XIII"
      slug: "f-louis"
      active: 0      

    - name: "Brutalist"
      slug: "f-brutalist"
      active: 0      

    - name: "Beaux-artes"
      slug: "f-beaux"
      active: 0

    # you can add more 
    - name: "name of architecture style"
      slug: "f-slug name"
      active: 0
```
<br>

## _works
`_works` is a collection having several markdown files (architecture contents).<br>
The collection `_works` has been specified in `config.yml`
``` ruby
# collections defined in config.yml
collections:
  - works #_works
  - further-reading #_further-reading
  - glossary #_glossary
  - docs #_docs
```

Each markdown files in `_works` will be rendered as one tile (card pop-up) in **`Buildings`** page. For example, the following shows the syntax of `art-nouveau-1.md`
``` ruby
---
title: art nouveau 1
category: Art Nouveau # should be the same as a target list value. ex) buildings.filters.name in settings.yml
category_slug: f-nouveau # must be the same as a target list value. ex) buildings.filters.slug in settings.yml
type: content # do not change
image: assets/img/works/work9.jpg # path to a picture you want
tags: [dormer-windows, Abacus] # tags linked to relevant entry in Glossary page
---

you can write some texts here...
```
<br><br>
**❗❗ Some important frontmatter rules in writing `.md` file in `_works` ❗❗**

<img src="/assets/img/docs/content-tile-ex.png" width="500">
<!-- ![pic1](/assets/img/docs/1.png){width=300px} -->

- the value of <code>category_slug</code> e.g., in `art-nouveau-1.md` must be the same as the value of a target list field in `settings.yml`
- please never change `type: content` e.g., in `art-nouveau-1.md`
- the value of <code>category</code> e.g., `art-nouveau-1.md` should be the same as the value of a target list field in `settings.yml`.
(This is just a recommention. They can go different, but having a make-sense & same naming is best practice as you wanna have more architecture categories & pics.)


<br><br>
**❗❗ How `Buildings` & `Glossary` page work  ❗❗**

- 1️⃣ user clicks a content tile and one of the tags in it.
- 2️⃣ the on-clicked tag then redirects user to a specific entry (heading) in `Glossary` page.

<br><br>
**❗❗ content tile (card pop-up) on hover  ❗❗**<br>
In `_sass/glitche/layout.scss`, find (ctrl + F) `.box-items` and check the updates.<br>
The CSS property `opacity` has been updated to adjust hover effect.

``` scss
  &:hover {
    .image {
      .info {
        opacity: 0.7; //0.94;
        @include transform(scale(1,1));
      }
    }
```


<br><br><br>
<hr>

# Glossary page
<br><br>

## glossary/index.html
imports the layout


## _layouts/glossary.html
`glossary.html` defines the page layout & structure 

## _glossary/glossary.md
`_glossary` is a collection directory set in `config.yml`<br>
The collection `_glossary` has been specified in `config.yml`
``` ruby
# collections defined in config.yml
collections:
  - works #_works
  - further-reading #_further-reading
  - glossary #_glossary
  - docs #_docs
```

`glossary.md` in `_glossary` is a markdown file that you can populate architecture glossaries in alphabetical order.

**Each heading MUST be a tag you set in `.md` files in `_works`**

<img src="/assets/img/docs/2.png" width="500">


<br><br><br>
<hr>

# Further Reading page
<br><br>

## further-reading/index.html
imports the layout


## _layouts/further-reading.html
`further-reading.html` defines the page layout & structure 

## _further-reading/further-reading-1.md
`_further-reading` is a collection directory set in `config.yml`<br>
The collection `_further-reading` has been specified in `config.yml`
``` ruby
# collections defined in config.yml
collections:
  - works #_works
  - further-reading #_further-reading
  - glossary #_glossary
  - docs #_docs
```

`further-reading-1.md` in `_further-reading` is a markdown file that has links to your external PDF and html page.

<br><br><br>
<hr>

# Header (Navigation)
<br><br>

## _data/navigation.yml
Based on your requirement, the following navigation is enabled, and you can change them at `_data/navigation.yml`

``` ruby
main:
  # Home
  - title: "Home"
    url: "/"
    button: 0

  # Buildings
  - title: "Buildings"
    url: "buildings/"
    button: 0
  
  # Glossary
  - title: "Glossary"
    url: "glossary/"
    button: 0

  # further reading
  - title: "Further Reading"
    url: "further-reading/"
    button: 0
```
<br>
## _sass/glitche/layout.scss
In this file, I changed <code>text-align: right;</code> to <code>text-align: left;</code> in `.header` css block.

You can customize it anytime.

<br><br><br>
<hr>

# sidebar visibility
sidebar is disabled for now as you don't want `Blog` page.
You can show or hide it at `_data/settings.yml`.

The field `sidebar` is a boolean, meaning that:
- 1 (true) shows the sidebar
- 0 (false) hides the sidebar

``` ruby
settings:
  quick_colors: "" # select quick color schemes: "blue", "green", "orange", "pink", "purple", "red". If empty colors taken from _sass/ryancv/settings.scss
  dark_ui: 0 # activated dark ui styles
  rtl: 0 # activated rtl styles
  sidebar: 0 # for disable sidebar and sidebar button change to 0
  preloader: "loading..." # preloader loading text
```

<br><br><br>
<hr>

# footer visibility
`footer` is removed as required.

At `_layouts/default.html`, you can disply it back by uncommenting (removing) the comment syntax of liquid as follows.
<img src="/assets/img/docs/footer.png" width="500">
<br>
Also, you can customize data in `footer` at `_data/footer.yml` anytime.
``` ruby
main:
  social:
    - title: "Dribbble"
      icon: "social-dribbble"
      url: "https://dribbble.com/"
    - title: "Twitter"
      icon: "social-twitter"
      url: "https://twitter.com/"
    - title: "GitHub"
      icon: "social-github"
      url: "https://github.com/"
    - title: "Instagram"
      icon: "social-instagram-outline"
      url: "https://instagram.com/"
  copy: "© 2020 Glitche. All rights reserved."
```


<br><br><br>
<hr>

# favicon
If you want to replace the existing favicon (website icon) with new one:
- pick your favorite picture or image, generate favicon at [https://realfavicongenerator.net/](https://realfavicongenerator.net/)
- download the package and find `favicon.ico`
- replace the existing `favicon.ico` with yours at the path `assets/images/favicons/`