---
layout: post  
title:  "Quick guide to hosting a free blog site on Github"  
date:   2022-08-06 19:58:40 +1000  
categories: github_pages jekyll  
tags: jekyll chirpy theme github_pages  
---

## Facts  
- This [site](https://andyshaoych.github.io/) is hosted on *Github Pages* with *Jekyll*    
- Jekyll in Ruby: Static site generator (Chirpy Theme)   
- Local workstation: **MacOS**  
- Tools: Visual Code / git / Ruby  
- Adding content (post) to the site: Markdown  

## Code and Docs  
  While a concise version of steps are stated below, refer to the following resources for more information.  
- 1) GitHub Pages doc (and Jekyll)  
  [https://docs.github.com/en/pages/quickstart](https://docs.github.com/en/pages/quickstart)
- 2) Chirpy Jekyll Theme code  
  [https://github.com/cotes2020/jekyll-theme-chirpy](https://github.com/cotes2020/jekyll-theme-chirpy)  
- 3) Chirpy Starter
  [https://github.com/cotes2020/chirpy-starter](https://github.com/cotes2020/chirpy-starter)
- 4) Chirpy Doc  
  [https://www.rubydoc.info/gems/jekyll-theme-chirpy/3.0.2](https://www.rubydoc.info/gems/jekyll-theme-chirpy/3.0.2)  
- 5) Reference (video)   
  [Meet Jekyll - The Static Site Generator](https://youtu.be/F8iOU1ci19Q)  

## Types of GitHub Pages sites  
- 3 types: user, organization, project  

- user / organization  
  - Repo: `<username/organization>.github.io`  
  - Site URL: `http(s)://<username/organization>.github.io`  
    (Unless you're using a **custom domain**)   

- project  
  - Repo: `project_repo`  
  - Site URL: `http(s)://<username/organization>.github.io/project_repo`  
    (Unless you're using a **custom domain**)   

- public / private repo?  
  `public / private`: GitHub Pro, GitHub Team, GitHub Enterprise   
  `public` only: GitHub Free for User/Organization   

## Install `Jekyll` and `Bundler`    
- Get the local environment ready with editor (e.g, Visual Code), git, and Ruby, etc.  
- Install Jekyll with `$ sudo gem install bundler jekyll`  
  ```bash
  $ sudo gem install bundler jekyll
    Password:
    Successfully installed bundler-2.3.19
    Parsing documentation for bundler-2.3.19
    Done installing documentation for bundler after 0 seconds
    Successfully installed jekyll-4.2.2
    Parsing documentation for jekyll-4.2.2
    Done installing documentation for jekyll after 0 seconds
    2 gems installed
  ```

## Create new repo on `github` and test locally    
- Notes  
  **Note**) The easiest way to create a new repository is mentioned in both doc `Chirpy Jekyll Theme code` and `Chirpy Starter`, which all point to this link [https://github.com/cotes2020/chirpy-starter/generate](https://github.com/cotes2020/chirpy-starter/generate). We'll follow the doc [Chirpy Jekyll Theme code](https://github.com/cotes2020/jekyll-theme-chirpy)  

  **Note**) Chirpy Jekyll Theme code `Chirpy Starter`:
  ![](/assets/images/hosting-a-free-blog-site-on-Github/2022-08-07-13-06-25.png)  

  **Note**) Chirpy Starter `Use this template`:
  ![](/assets/images/hosting-a-free-blog-site-on-Github/2022-08-07-13-06-50.png)  

- Creating a New Repo by click on [Chirpy Starter](https://github.com/cotes2020/chirpy-starter/generate)  
  (Make sure have github logged in first)  
  Name the Repo as `<USERNAME>.github.io`  
  Make it as Public  
  ![](/assets/images/hosting-a-free-blog-site-on-Github/2022-08-07-13-18-46.png)  

- Verify the created code (with default `main` branch only)  
  ![](/assets/images/hosting-a-free-blog-site-on-Github/2022-08-07-21-16-33.png)   

- `git clone` the repo to your local  
  ```bash
    git clone https://github.com/andyshaoych/<USERNAME>.github.io.git  
  ```
  ![](/assets/images/hosting-a-free-blog-site-on-Github/2022-08-07-13-35-56.png)  

- Update .gitignore with `.DS_Store` & `.vscode` in case of MacOS   
  ![](/assets/images/hosting-a-free-blog-site-on-Github/2022-08-07-14-40-27.png)  

- Installing Dependencies by `bundle`    
  ```bash
    $ cd andyshaoych.github.io/
    $ bundle
      Fetching gem metadata from https://rubygems.org/...........
      Resolving dependencies...
      ...
      Using jekyll-theme-chirpy 5.2.1
      Bundle complete! 6 Gemfile dependencies, 44 gems now installed.
      ...
  ```

- Running Local Server by `bundle exec jekyll serve`  
  ```bash
  $ bundle exec jekyll serve
    Configuration file: /Users/andy.shao/andy_workplace/andyshaoych.github.io/_config.yml
    Theme Config file: /Library/Ruby/Gems/2.6.0/gems/jekyll-theme-chirpy-5.2.1/_config.yml
                Source: /Users/andy.shao/andy_workplace/andyshaoych.github.io
          Destination: /Users/andy.shao/andy_workplace/andyshaoych.github.io/_site
    Incremental build: disabled. Enable with --incremental
          Generating... 
                        done in 1.711 seconds.
    Auto-regeneration: enabled for '/Users/andy.shao/andy_workplace/andyshaoych.github.io'
        Server address: http://127.0.0.1:4000/
      Server running... press ctrl-c to stop.
  ```

  - Optional) Run with Docker:
    ```bash
    $ docker run -it --rm \
        --volume="$PWD:/srv/jekyll" \
        -p 4000:4000 jekyll/jekyll \
        jekyll serve
    ```

- Verify the empty site working   
  (we'll come back to add content after deploying on GitHub Pages)  
  ![](/assets/images/hosting-a-free-blog-site-on-Github/2022-08-07-14-00-06.png)  

## Deploy on GitHub Pages   
- Note) Follow the steps here strictly although you may refer to the following docs for information:       
  Refer to [Chirpy Doc](https://www.rubydoc.info/gems/jekyll-theme-chirpy/3.0.2) (skill other sections until `Deploy on GitHub Pages`)   
  Refer to `Deploy on Other Platforms` on the same page if interested in.   

- Verifications   
  - Verify your GitHub Pages is with the default branch (`main`) as the `Source`  
    ![](/assets/images/hosting-a-free-blog-site-on-Github/2022-08-07-14-48-18.png)  

  - Verify your site is shown as the following   
    ![](/assets/images/hosting-a-free-blog-site-on-Github/2022-08-07-14-49-34.png)   

  - Verify `/.github/workflows/pages-deploy.yml`   
    `on.push.branches` should be the repo's default branch name (`main`).   
    The file will be used by `GitHub Actions` to build site files.  
    ```yaml
      name: 'Automatic build'
      on:
        push:
          branches:
            - main
    ```
    ![](/assets/images/hosting-a-free-blog-site-on-Github/2022-08-07-14-35-22.png)  

- **IMPORTANT**) Add platform `x86_64-linux` to `lockfile`  
  Otherwise the `GitHub Actions workflow` will fail.  
  ```bash
    $ bundle lock --add-platform x86_64-linux
      Fetching gem metadata from https://rubygems.org/.........
      Resolving dependencies...
      Writing lockfile to /Users/andy.shao/andy_workplace/andyshaoych.github.io/Gemfile.lock
  ```

  - Gemfile.lock   
    ```yaml
      PLATFORMS
        universal-darwin-21
        x86_64-linux
    ```
    ![](/assets/images/hosting-a-free-blog-site-on-Github/2022-08-07-20-40-16.png)  

- Commit and push the code up to GitHub  
  ```bash
    $ git add . 
    $ git commit -m "first update"
    $ git push
  ```

- Make sure `pages-deploy.yml` workflow under `GitHub Actions` build successfully done.   
  Our `pages-deploy.yml` workflow will displayed as `your git commit message`, which triggered via push and built`gh-pages` branch:  
  ![](/assets/images/hosting-a-free-blog-site-on-Github/2022-08-07-20-48-05.png)   
  ![](/assets/images/hosting-a-free-blog-site-on-Github/2022-08-08-09-05-31.png)  
  ![](/assets/images/hosting-a-free-blog-site-on-Github/2022-08-08-09-06-35.png)  
  ![](/assets/images/hosting-a-free-blog-site-on-Github/2022-08-08-09-06-53.png)  

- Verify `gh-pages` branch is created by the above workflow, to store the built `site` files.  
  ![](/assets/images/hosting-a-free-blog-site-on-Github/2022-08-07-21-05-57.png)   

  Similar to the local `_site` folder  
  ![](/assets/images/hosting-a-free-blog-site-on-Github/2022-08-07-21-08-32.png)  

- Select GitHub Pages source to `gh-pages` branch:   
  Settings → Options → GitHub Pages → Save  
  ![](/assets/images/hosting-a-free-blog-site-on-Github/2022-08-07-21-23-04.png)

- Verify workflow `pages build and deployment` build successfully done.   
  Triggered via GitHub Pages (bot) and build `github.io` site.  
  ![](/assets/images/hosting-a-free-blog-site-on-Github/2022-08-08-09-19-27.png)  
  ![](/assets/images/hosting-a-free-blog-site-on-Github/2022-08-08-09-19-46.png)  

- Verify the newly deployed site   
  Note) This deployment is done by GitHub Pages workflow 
  ![](/assets/images/hosting-a-free-blog-site-on-Github/2022-08-07-21-37-39.png)   

## Add a new post to the site with Markdown  
- Add a Markdown file to `_posts` with naming convention as `YYYY-MM-DD-NAME-OF-POST.md`, e.g,  
  `2022-08-06-hosting-a-free-blog-site-on-Github.md`  

- YAML frontmatter  
  Add frontmatter to the **first** line   
  ```
    ---
    layout: post  
    title:  "Quick guide to hosting a free blog site on Github"  
    date:   2022-08-06 19:58:40 +1000  
    categories: github_pages jekyll  
    tags: jekyll chirpy theme github_pages  
    ---
  ```
  ![](/assets/images/hosting-a-free-blog-site-on-Github/2022-08-07-22-56-12.png)  

- Populate image files to `Asset` and update the image links, e.g.:    
  `![](/assets/images/hosting-a-free-blog-site-on-Github/2022-08-07-21-37-39.png)`   
  ![](/assets/images/hosting-a-free-blog-site-on-Github/2022-08-07-22-59-41.png)  

- Verify at local  
  ![](/assets/images/hosting-a-free-blog-site-on-Github/2022-08-07-23-15-53.png)  

## Customize the site via `_config.yml`  
- Update the variables of _config.yml  
  ```
    avatar: /assets/images/avatar.png

    timezone: Australia/Sydney
    title: DevOps                          # the main title
    tagline: Andy Shao's Tech Notes   # it will display as the sub-title

    github:
      username: andyshaoych             # change to your github username

    social:
      name: Andy Shao
        - https://github.com/andyshaoych       # change to your github homepage
        - https://www.linkedin.com/in/andyshao
  ```
  
- Commit and push the code up to GitHub  
  ```bash
    $ git add . 
    $ git commit -m "first update"
    $ git push
  ```

- Verify the GitHub Actions  


- Verify on GitHub Pages site   

  ![](/assets/images/hosting-a-free-blog-site-on-Github/2022-08-08-00-03-02.png)   

  ![](/assets/images/hosting-a-free-blog-site-on-Github/2022-08-08-00-03-42.png)  

  ![](/assets/images/hosting-a-free-blog-site-on-Github/2022-08-08-00-03-59.png)  

  ![](/assets/images/hosting-a-free-blog-site-on-Github/2022-08-08-00-04-12.png)  

## (Optional) Monetizing a Jekyll blog with Adsense  
  [https://ncona.com/2020/11/monetizing-a-jekyll-blog-with-adsense/](https://ncona.com/2020/11/monetizing-a-jekyll-blog-with-adsense/)  
