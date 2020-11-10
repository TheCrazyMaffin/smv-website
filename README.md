# Variables
Use `{{ var }}` to embed a variable on a page.

Use `{? code ?}` to embed ruby code.

Introduce variables to a file by adding them in between the two `---` marks. (Thats called "Front Matter") Access them using `page.*name*`.

## Global variables
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

# _includes
Add snippets from this folder using `{% include foobar.html %}`

To be continued here https://jekyllrb.com/docs/step-by-step/09-collections/

and here https://github.com/pages-themes/cayman/blob/master/_layouts/default.html