# Variables
Use `{{ var }}` to embed a variable on a page.

Use `{? code ?}` to embed ruby code.

Introduce variables to a file by adding them in between the two `---` marks. (Thats called "Front Matter") Access them using `page.*name*`.

# Filters
When inserting variables into e.g. layouts (You'll learn more about this later) you will use `{{ foobar }}`. You can apply filters before inserting this variable. For example a posts content will automatically be markdownified when using `{{ content }}`. If you were to markdownify any other variable like `collectionElement.content` you need to use filters like this. `{{ variable | filter}}` (Here: `{{ collectionElement.content | markdownify }}`)

## Variables
| Variable | Property | Description |
| --- | --- | --- |
| site | | Side wide information and config from `_config.yml` |
| | time | Build time |
| | pages | List of all pages |
| | posts | Reverse chronological list of all posts. A post object has the properties `url`, `title`, `excerpt` (The first paragraph of the content) |
| | related_posts | The ten most recent posts |
| | static_files | All files without front matter.  Has the properties `path`, `modified_time`, `name`, `basename`, `extname`. |
| | html_pages | All `site.pages` which end in `.html`
| | html_files | All `site.static_files` which end in `.html` |
| | collections | List of all collections |
| | data | All data loaded from YAML files in the `_data` directory |
| | documentes | All documents in every collection |
| | category.*NAME* | A list of all posts in the category *Name* |
| | tags.*TAG* | All posts with the tag *TAG* |
| page | | Page specific information and the front matter variables | 
| | content | The content of the page |
| | title | The title of the page |
| | excerpt | Un-rendered excerpt of the page |
| | url | URL without the domain |
| | date | The date of a post |
| | id | Unique identifier |
| | categories | The page categories |
| | collection | Collection this page is part of |
| | tags | Tags specified in front matter variables |
| | dir | Path between the source directory and the page
| | name | Filename of the page |
| | path | Link to the raw file |
| | next | The next post from `site.posts` |
| | previous | The previous post from `site.posts` |
| layout | | Layout specific information. Front matter variables of the layout file will be in this variable. |
| content | | Content for layout files. Undefined in posts or pages |

# _layouts
This folder holds all layouts available on the page. The layout to be used on a page is defined by the `layout` variable on said page.

The `{{ content }}` variable in a layout file will later be replaced by the content of the page it is used on.

Layouts can inherit other layouts. Defining `layout` in the front matter of a layout file does work.

# _includes
Add snippets from this folder using `{% include foobar.html %}`

# _data
JSON, YAML or CSV files may live here. Access it's contents using `site.data.*NAME*`

# _sass
Jekyll uses [SASS](https://sass-lang.com/guide). Add empty front matter at the top of each file so that Jekyll knows it needs to process the file. 

You may use `@import foobar` in a `.scss` file to import the contents of the file `_sass/foobar.scss`.

`.scss` files with the empty front matter at the top will be processed into `.css` files an can be accessed at their original location.

# _posts
The filename of a post will include the date, the name and an extension. (e.g. `2020-11-12-xmas.md` or in general `yyyy-mm-dd-title.xy`)

Posts also require front matter. You will at least need to include a `layout` variable. You may use other variables such as `author` or similar to use in the layout.

# Collections
Each collection needs to be defined in the `_config.yml` using
```
collections:
    foobar:
```
and needs a folder in the root of the project named `_foobar` (matching the name of the collection)

`site.*NAME*` (Here `site.foobar`) will hold all pages put into the collections folder. One object of the collection will have the property `content` aswell as all the variables defined in the front matter.

If
```
collections:
    foobar:
        output: true
```
is set for collections they will have their own page which can be reached by using the link `{{ foobar.url }}` (`foobar` being the collection name)

# Defaults

You can set defaults in `_config.yml`. Just like this:
```
defaults:
    - scope:
        path: ""
        type: "collectionName"
    values:
        layout: "someLayoutToBeUsed"
    - scope:
        path: ""
        type: "posts"
    values:
        layout: "post"
    - scope:
        path: ""
    values:
        layout: "default"
```

# Debugging
Start a debugging server using
```
bundle exec jekyll serve --live
```

## Problems with eventmachine?
```
gem uninstall eventmachine
gem install eventmachine --platform ruby
```

## Material Icons
1. Look them up [here](https://material.io/resources/icons/)
2. Copy the `code` and paste it.

## Member cards
To get listed on the member page simply do the following
1. Put a image of yourself in `assets/images/members` and name it `firstname_lastname.png` while png may aswell be any other extension modern browsers can show. Remember the filename
2. Create a file named `lastname_firstname.md` in the folder `_members`
3. Put this in the file
```
---
name: Firstname Lastname
position: Verbindungslehrer | Schülersprecher | Mitglied <-- Pick one of the three and remove this comment and all the non applicable choices.
image: lastname_firstname.png <-- Put the filename of your image from step 1 here and remvoe this comment.
---
Write something about you. Do it and remove this comment.
```

## Events
**Template:**
```
---
title: TITLE HERE
date:  yyyy-mm-dd
layout: event
---
First paragraph should be relatively short. This is what will be displayed on the front page.
```
Name the file so that people recognize it later. The first paragraph is displayed on the front page so make it short and with alot of information

## Galerie
Just place image files in `/gallery/`. Done.




To be continued here https://jekyllrb.com/docs/step-by-step/09-collections/

and here https://github.com/pages-themes/cayman/blob/master/_layouts/default.html