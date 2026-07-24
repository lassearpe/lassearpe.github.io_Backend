Build process: 

Make changes to the backend in a markdown document for each blog post. 

Build this with "sudo bundle exec jekyll build". 

Go into the frontend, `_site` folder, and now add, commit, and push the build changes.



Update: DEPLOY _site STATIC FILES TO lassearpe.github.io:
```
cd _site

git init
git add .
git commit -m "Deploy website"

git branch -M main
git remote add origin https://github.com/lassearpe/lassearpe.github.io.git
git push -f origin main
``