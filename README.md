# Notifications Page - Vue Cli and Tailwind CSS

## Project Challenge
Front Mentor [click here](https://www.frontendmentor.io/challenges/notifications-page-DqK5QAmKbC/hub)

## Project Setup 
install Vue CLI ```npm install -g @vue/cli```

create project ```vue create nama_project```

install Tailwind CSS ```npm install -D tailwindcss```

run project ```npm run serve```

## Deploy Project GithubPages
1. setting vue.config.js

```
const { defineConfig } = require('@vue/cli-service')
module.exports = defineConfig({
  transpileDependencies: true,
  publicPath: "/name-repository/"
})
```

2. create file ```deploy.sh```

```
#!/usr/bin/env sh 
# abort on errors 
set -e 

#build 
npm run build 

cd dist 

git init 
git add -A 
git commit -m "deploy"  
git push -f git@github.com:<username>/<name-repository>.git master:deploy 

cd -
```

3. setting package.json
```"deploy": "sh deploy.sh"```

4. run in terminal ```npm run deploy```

5. check github_pages

## Link Github Pages
[Github Pages](https://abdulmuktinur.github.io/VueJs-Notifications/)
