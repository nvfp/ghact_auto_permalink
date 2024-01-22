Make your blog-like pages' permalink automatically written during the build, which means we just need to specify the URL in the directory project structure, and the permalink will be based on that, which saves time!

The project structure should look like this:

```txt
root/
- foo/
  - bar/
    - 2020/
      - 01-01-title_1/
        - index.md
        - img.jpg
        - ...
      - 01-01-title_2/
        - index.md
        - ...
    - 2021/
      - ...
```

Let's say this is a blog project, so each post has its own folder, `root/foo/bar/2020/01-01-title_1/` for example (let's call this "container"). So each post should have `index.md`, which contains the blog content itself. Inside each container, it can also contain images or anything needed for that specific post. Also, they will be grouped by years, so things are more maintainable for a long period project.

Now let's open one of the containers:

```markdown
---
# permalink:  # leave this empty because it will be written during the build process

... # the rest of the file
```

So, we just need to specify the commented `permalink` at line `2`, then during the build, we will be using:

```yml
- uses: nvfp/ghact_auto_permalink@a.b.c  # using the latest version OR main-branch is recommended
  with:
    where: ./foo/bar  # "bar" is the "root" for the blog-like pages
    prefix: /blog/  # to make it "/blog/title_1", "/blog/title_2", etc.
```

Note: Please open the `action.yml` to learn more about the params.

And that's it!
