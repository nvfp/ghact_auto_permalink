Make your blog-like pages' permalink automatically written during the build, which means we just need to specify the URL in the directory project structure, and the permalink will be based on that, which saves time!

The project structure should look like this

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

let's say this is a blog project, so, each post has its own folder, `root/foo/bar/2020/01-01-title_1/` for example (let's call this as "container"). so each post should have `index.md` which contain the blog content itself. inside each container, can also contain images or anything needed for that specific post. also they will be grouped by years, so things more maintainable for long period project.

now let's open one of the container:

```markdown
---
# permalink:  # leave this emoty becuase will be ritten during build process

... # the rest of the file
```

so, we just need to specify the commented `permalink` at the line `2`, then during the build, we will be using:

```yml
- uses: nvfp/ghact_auto_permalink@a.b.c  # use the latest version is recommended
  with:
    where: ./foo/bar  # bar is the "root" for the blog-like pages
```

Note, please open the `action.yml` for learn morea bout the params.

and that's!

## Lincese

MIT Lincense. feel free to use the code as youwould like, have a great day!