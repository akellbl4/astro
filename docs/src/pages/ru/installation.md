---
layout: ~/layouts/MainLayout.astro
title: Установка
description: Как установить Astro с NPM, PNPM или Yarn.
---

Есть несколько разных путей для создания нового проекта с Astro.

## Предустановки

- **Node.js** - `v12.20.0`, `v14.13.1`, `v16.0.0`, or higher.
- **Текстовый редактор** - We recommend [VS Code](https://code.visualstudio.com/) with our [Official Astro extension](https://marketplace.visualstudio.com/items?itemName=astro-build.astro-vscode).
- **Терминал** - Astro is mainly accessed via the terminal's command-line.

For demonstration purposes, we will be using [`npm`](https://www.npmjs.com/) in the examples below, but you could also use [`yarn`](https://yarnpkg.com/) or [`pnpm`](https://pnpm.io/) if you prefer an npm alternative.

## Установщик Astro

`npm init astro` is the easiest way to install Astro in a new project. Run this command in your terminal to start our `create-astro` install wizard to assist you with setting up a new project.

```shell
# With NPM
npm init astro

# Yarn
yarn create astro

# Pnpm
pnpm create astro
```

[`create-astro`](https://github.com/snowpackjs/astro/tree/main/packages/create-astro) wizard lets you choose from a set of [starter templates](https://github.com/snowpackjs/astro/tree/main/examples) or alternatively, you could import your own Astro project directly from GitHub.

```bash
# Note: Replace "my-astro-project" with the name of your project.

# npm 6.x
npm init astro my-astro-project --template starter
# npm 7+ (extra double-dash is needed)
npm init astro my-astro-project -- --template starter
# yarn
yarn create astro my-astro-project --template starter
# pnpm
pnpm create astro my-astro-project --template starter
# Using a third-party template
npm init astro my-astro-project -- --template [GITHUB_USER]/[REPO_NAME]
# Using a third-party template, inside a repo
npm init astro my-astro-project -- --template [GITHUB_USER]/[REPO_NAME]/path/to/template
```

After `create-astro` scaffolds out your project, remember to install your projects dependencies using npm or your package manager of choice. In this example, we'll use npm:

```bash
npm install
```

You can now [Start](#start-astro) your Astro project. Once you have completed assembling your Astro project you can then [Build](#build-astro) your project. Astro would then package up your application and have the static files ready for you to [Deploy](/guides/deploy) to your favourite hosting provider.

## Ручная установка

You can also set up Astro without the aide of the `create-astro` wizard, below are the few extra steps that are required to get Astro going.

### Подготовка проекта

```bash
# Make and enter a new directory
mkdir my-astro-project
cd my-astro-project
```

Create an empty directory with the name of your project, and then navigate into it:

### Создание `package.json`

```bash
# This command will create a basic package.json for you
npm init --yes
```

Astro is designed to work with the entirety of the npm package ecosystem. This is managed by a project manifest at the root of your project known as `package.json` . If you're not familiar with the `package.json` file, we highly recommend you to have a quick read over it on [the npm documentation](https://docs.npmjs.com/creating-a-package-json-file).

### Установка Astro

Following the instructions above, you should have a directory with a single `package.json` file inside of it. You can now set up Astro inside your project.

```bash
npm install astro
```

You can now replace the placeholder "scripts" section of your `package.json` file that `npm init` created for you with the following:

```diff
  "scripts": {
-    "test": "echo \"Error: no test specified\" && exit 1"
+    "dev": "astro dev",
+    "build": "astro build",
+    "preview": "astro preview"
  },
}
```

The [`dev`](#start-astro) command launches the Astro Dev Server on `http://localhost:3000`. Once your project is ready, the [`build`](#build-astro) command outputs your project to the `dist/` directory. [Read more about deploying Astro in the Deploy guide.](/guides/deploy)

### Создаем первую страницу

Astro Open up your favourite text editor, and create a new file in your project:

1. Create a new file at `src/pages/index.astro`
2. Copy-and-paste the following snippet (including `---` dashes) into it.

```astro
---
// JS/TS Code written in between the (---) code fence,
// is ran solely on the Server!
console.log('See me in the Terminal')
---

<html>
  <body>
    <h1>Hello, World!</h1>
  </body>
</html>

<style lang='css||scss'>
  body{
    h1{
      color:orange;
    }
  }
</style>

<script>
 // JS Code entered here is ran entirely on the Browser
 console.log('See me in the devTools')
</script>
```

Above is an example of the Astro's Component's Syntax, which comprises of both HTML & JSX.

You can create more pages in the `src/pages` directory, and Astro will use the filename to create new pages on your site. For example, by creating a new file at `src/pages/about.astro` (reusing the previous snippet), Astro will generate a new page at the URL : `http://localhost/about`

## [Запуск Astro](#start-astro)

```bash
npm run dev
```

Astro will now start serving your application on `http://localhost:3000`. By opening this URL in your browser, you should see the Astro's “Hello, World”.

If you need to share your development progress on the local network or check out the app from a phone, just add the following [snowpack](https://www.snowpack.dev/reference/configuration#devoptionshostname) option to `astro.config.mjs`:

```js
devOptions: {
  hostname: '0.0.0.0';
}
```

## [Сборка Astro](#build-astro)

```bash
npm run build
```

This will instruct Astro to build your site and save it directly to disk. Your application is now ready in the `dist/` directory.

## Следующие шаги

Ура! Теперь вы готовы к разработке!

Мы рекомендуем вам потратить немного времени, чтобы познакомиться с работой Astro ближе. Вы можете сделать это с помощью дальнейшего ознакомления с документацией. Мы советуем изучить следующие материалы:

📚 Узнать больше [о структуре проектов Astro.](/core-concepts/project-structure)

📚 Узнать больше [о синтаксисе компонентов Astro.](/core-concepts/astro-components)

📚 Узнать больше [о роутинге, основанном на файловой структуре.](core-concepts/astro-pages)
