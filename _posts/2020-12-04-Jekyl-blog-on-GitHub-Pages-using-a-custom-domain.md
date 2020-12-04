# Introduction
Quick instructions on how to create a Jekyl blog via GitHib pages and redirecting your custom domain from AWS to it

Sources:
- [https://benwiz.com/blog/deploy-github-pages-with-aws-route-53-and-https/](https://benwiz.com/blog/deploy-github-pages-with-aws-route-53-and-https/)
- [https://christopherkade.com/posts/subdomain-githubpages](https://christopherkade.com/posts/subdomain-githubpages)
- [https://talk.hyvor.com/blog/creating-a-static-site-blog-with-jekyll-and-github-pages/](https://talk.hyvor.com/blog/creating-a-static-site-blog-with-jekyll-and-github-pages/)


# Steps

## 1. Create new GitHub repository and enable GitHub Page

1. Create a new repository using the following format: `<YOUR USERNAME>.github.io`.
2. Go to your newly created repo and go to settings.
3. Scroll down to the GitHub Pages section and enable by selecting `Branch: main`.
4. Check Enforce HTTPS

## 2. Create a placeholder website

1. Clone the repo `git clone https://github.com/<USERNAME>/<USERNAME>.github.io.git`.
2. Change directory `cd <USERNAME>.github.io.git`
3. Create a basic placeholder index.html `echo "Hello GitHub Pages!" > index.html`
4. Create a CNAME file with the domain you want to forward to `<DOMAIN> > CNAME`
5. Push to GitHub `git add . && git commit -m 'Initial commit - placeholder index and CNAME' && git push`


## 3. Configure AWS Route 53 to point to your website

1. Log into AWS console and go to the Route 53 dashboard
2. Click *Hosted zones*
3. Click the domain you would like to use
4. Click *Create Record*
5. Click *Simple Routing > Next*
6. Click *Define simple record*
7. For *record name* enter in the subdomain e.g. `blog.dominicst.com`
8. For *Value/Route traffic* from the drop-down menu select *IP address or another value, depending on the record type*. In the free text box enter in your GitHub pages URL i.e.  `<USERNAME>.github.io`
9. For *Record type* select *CNAME*
10. Select *Define simple record*
11. Head to your domain to see if it loads your GitHub page.


## 4. Set up jekyll


1. [Install ruby](https://www.ruby-lang.org/en/documentation/installation/#apt)
2. Install Jekyl `gem install jekyll bundler`
3. `jekyll new .` - You might need to delete and remake the CNAME file.
4. Use `bundler exec jekyll serve` to run locally on [http://localhost:4000](http://localhost:4000)
5. Edit the config file `_config.yml` 
6. Start creating blog posts in the *_posts* folder, file names should be in the `YEAR-MONTH-DAY-title.md` format




