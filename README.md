CRD Talks
=========

**CRD Talks** is a static site built on [jekyll][jekyll] that houses tutorials, write-ups, and case studies for the CRD department.

It's github-powered, so any one of us can (and should!) contribute.

Contributing
------------

1. Clone the project: `git clone git@github.com:SFCRD/sfcrd.github.com.git`.

2. Install the dependencies: `bundle install`

3. Run `rake jekyll`. This starts the jekyll server in watch mode at `http://localhost:4000`.

4. Change something, or make a new post in `_posts`. Follow the naming convention plz kthx.

5. To update the YAML frontmatter for all posts, run `rake frontmatter`.

6. Push the changes back up to the repo: `git push origin master`.

Once you push changes to master, github will rebuild the site automatically. Pretty neat!

Todos
-----

- Add in Disqus comments to each post.

- Come up with a better name for the site? 'CRD Talks' kinda blows...

[jekyll]: https://github.com/mojombo/jekyll
