# —AUTO—Deploy Docusaurus on GitHub Action

---

環境:Win 11

---

1. Create your GitHub Repo
2. Open CMD: 
    
    

```jsx
git clone https://github.com/<User-Name>/<Repo-Name>.git //make a Folder of your GitHub repo

code .\<Repo-Name>.\   //use VScode to open your folder
```

1. Open the Terminal in your VScode:

```jsx
yarn  create docusaurus . classic --typescript

yarn start //test

yarn build //generate build Folder
```

1. To set your global username/email configuration:
Open the command line.

```jsx
Set your username:
git config --global user.name "FIRST_NAME LAST_NAME"

Set your email address:
git config --global user.email "MY_NAME@example.com"
```

1. Left sideBar Open Source Control:
    
    COMMIT: feat: generate Docusaurus website
    
2. Configure your docusaurus.config.js

```jsx
url: 'https://<user>.github.io'
 
trailingSlash: false   //--------------Add------both true or false is Ok--------// 

baseUrl: '/cdz1223_web/' <optional>

organizationName: '<Github-User-Name>', // Usually your GitHub org/user name.

projectName: '<Github-Repo-Name>', // Usually your repo name.
```

1. Terminal:

```jsx
yarn build
```

-- Github Action -------------------------------------------------------—

1. Left sideBar Open Source Control:

COMMIT:

chore: configure Docusaurus  

 
Change Sync  


build a new folder .github at the Root of your Folder    


build a new folder workflows in the .github Folder    


build a file "[Name]".yml in .github/worlflows    


:::tip

to Github>>setting>>pages>>[Build and deployment>>Source>>GitHub Action] 

[optional]:>>to Github>>setting>>Enviroment>>click [github-pages]>>[require reviewers] add your self

:::

1. Edit your .yml

```jsx
# Simple workflow for deploying static content to GitHub Pages
name: Deploy static content to Pages

on:
  # Runs on pushes targeting the default branch
  push:
    branches: [main]

  # Allows you to run this workflow manually from the Actions tab
  workflow_dispatch:

# Sets permissions of the GITHUB_TOKEN to allow deployment to GitHub Pages
permissions:
  contents: read
  pages: write
  id-token: write

# Allow one concurrent deployment
concurrency:
  group: "pages"
  cancel-in-progress: true

jobs:
  # Single deploy job since we're just deploying
  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v3
      - name: Set up Node.js
        uses: actions/setup-node@v3
        with:
          node-version: 18.x
          cache: yarn
      - name: Install dependencies
        run: yarn install --frozen-lockfile  --non-interactive
      - name: Build
        run: yarn build
      - name: Setup Pages
        uses: actions/configure-pages@v3
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v1
        with:
          # Upload entire repository
          path: 'build'
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v1
```

1. Left sideBar Open Source Control:

COMMIT:ci: set up deployment workflows

Change Sync

Check your GitHub action(IF with a  Green Hook it is complete)

---

You are finish Auto Deployment to GitHub.

:::tip

when you change any file and you need to upload to your website 

Just:

COMMIT:

(Remember type the Descreption.)

:::