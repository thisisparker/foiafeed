# FOIAFeed

## This project has been archived, and development moved to [Track The News](https://github.com/freedomofpress/trackthenews), a general bot framework that now powers @FOIAFeed and others. The information below should be considered out of date.

`foiafeed.py` is the script that powers [@FOIAfeed](https://twitter.com/foiafeed), a Twitter bot that monitors news outlets for reporting that incorporates public records laws like the Freedom of Information Act (FOIA), and tweets links to and excerpts from matching articles.

Most of the script is dedicated to the `Article` class.
* `Article`s are created based on inputs. Currently those inputs are RSS feeds, which are stored in `rssfeeds.json`, but in future versions other inputs will include direct URLs, news APIs, Twitter feeds, or scraped pages.
* A series of `Article` methods then scrape and isolate the contents of each article (currently that cleanup is done with a [Python port of Readability](https://github.com/buriy/python-readability), but future versions may incorporate some per-site parsing), check whether it's suitable for posting, and then prepare images for tweeting.
* Finally, the `Article` tweets itself.

All articles are recorded in a sqlite database defined by the `schema.sql` file.
