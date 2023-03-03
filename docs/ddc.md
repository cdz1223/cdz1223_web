# Docsaurus Deploy on GitHub

# Download Node.js

[https://nodejs.org/zh-tw/download/](https://nodejs.org/zh-tw/download/)

---

# Download git

[git-scm.com/downloads](https://link.juejin.cn/?target=https%3A%2F%2Fgit-scm.com%2Fdownloads)

---

# 設定Docsaurus

```jsx
npm init docusaurus
```

輸入你的網頁名稱後，一路Enter/確認 即可(也可自行設定你需要的選項)

```jsx
cd <your website folder>

npm start //在Local端查看你的Website
```

---

設置(docusaurus.config.js)

```jsx
// @ts-check
// Note: type annotations allow type checking and IDEs autocompletion

const lightCodeTheme = require('prism-react-renderer/themes/github');
const darkCodeTheme = require('prism-react-renderer/themes/dracula');

/** @type {import('@docusaurus/types').Config} */
const config = {
  title: 'My Site', //網站索引
  tagline: 'Dinosaurs are cool',//網站內標語
  favicon: 'img/favicon.ico',//網站索引小圖片

  // Set the production url of your site here
  **url:'https://<GitHub_name>.github.io'**
  // Set the /<baseUrl>/ pathname under which your site is served
  // For GitHub pages deployment, it is often '/<projectName>/'
  baseUrl: '/', //<optional>

  // GitHub pages deployment config.
  // If you aren't using GitHub pages, you don't need these.
  **organizationName: '<GitHub_name>', // Usually your GitHub org/user name.
  projectName: '<GitHub_Repositories_name>', // Usually your repo name.
	
	deploymentBranch: 'gh-pages', // !!!!MUST
  trailingSlash: false,////!!!MUST**

	
  onBrokenLinks: 'throw',
  onBrokenMarkdownLinks: 'warn',

  // Even if you don't use internalization, you can use this field to set useful
  // metadata like html lang. For example, if your site is Chinese, you may want
  // to replace "en" with "zh-Hans".
  i18n: {
    defaultLocale: 'en',
    locales: ['en'],
  },

  presets: [
    [
      'classic',
      /** @type {import('@docusaurus/preset-classic').Options} */
      ({
        docs: {
          sidebarPath: require.resolve('./sidebars.js'),
          // Please change this to your repo.
          // Remove this to remove the "edit this page" links.
         // editUrl:
           // 'https://github.com/facebook/docusaurus/tree/main/packages/create-docusaurus/templates/shared/',
        },
        blog: {
         showReadingTime: true,
          // Please change this to your repo.
          // Remove this to remove the "edit this page" links.
         // editUrl:
           // 'https://github.com/facebook/docusaurus/tree/main/packages/create-docusaurus/templates/shared/',
        },
        theme: {
          customCss: require.resolve('./src/css/custom.css'),
        },
      }),
    ],
  ],

  themeConfig:
    /** @type {import('@docusaurus/preset-classic').ThemeConfig} */
    ({
      // Replace with your project's social card
      image: 'img/docusaurus-social-card.jpg', //NavBar圖片
      navbar: {
        title: 'My Site',
        logo: {
          alt: 'My Site Logo',
          src: 'img/logo.svg',
        },
        items: [
          {
            type: 'doc',
            docId: 'intro',
            position: 'left',
            label: 'Tutorial',
          },
          {to: '/blog', label: 'Blog', position: 'left'},
          {
            href: 'https://github.com/facebook/docusaurus',
            label: 'GitHub',
            position: 'right',
          },
        ],
      },
      footer: {
        style: 'dark',
        links: [
          {
            title: 'Docs',
            items: [
              {
                label: 'Tutorial',
                to: '/docs/intro',
              },
            ],
          },
          {
            title: 'Community',
            items: [
              {
                label: 'Stack Overflow',
                href: 'https://stackoverflow.com/questions/tagged/docusaurus',
              },
              {
                label: 'Discord',
                href: 'https://discordapp.com/invite/docusaurus',
              },
              {
                label: 'Twitter',
                href: 'https://twitter.com/docusaurus',
              },
            ],
          },
          {
            title: 'More',
            items: [
              {
                label: 'Blog',
                to: '/blog',
              },
              {
                label: 'GitHub',
                href: 'https://github.com/facebook/docusaurus',
              },
            ],
          },
        ],
        copyright: `Copyright © ${new Date().getFullYear()} My Project, Inc. Built with Docusaurus.`,
      },
      prism: {
        theme: lightCodeTheme,
        darkTheme: darkCodeTheme,
      },
    }),
};

module.exports = config;
```

---

# 網站部屬(Deploy)

```jsx
npm run build //生成靜態網頁
```

```jsx
npm run serve //在local端測試
```

# GitHub操作:

:::danger

💡 在GitHub建立**Repositories (需要與上面的<GitHub_Repositories_name>相同)**

::: 

在Terminal輸入

```jsx
cmd /C "set GIT_USER=<GitHub_username>&& yarn deploy"
```

你就可以回到你的**Repositories查看是否多一個Branches(有就成功了)**

最後到 **https://<GitHub_name>.github.io 就可以看到網頁成功建立了**