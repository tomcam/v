# v
VuePress notes

## Creating a minimal custom theme

Custom theme

### Set up directories in /usr/local/lib/node_modules

Custom themes live in the directory /usr/local/lib/node_modules, so create it and change to that directory:

```bash
$ sudo mkdir -p /usr/local/lib/node_modules/vuepress-theme-bare/.vuepress
$ cd /usr/local/lib/node_modules/vuepress-theme-bare
```

### Create the file Layout.vue

Add this file to the theme directory and name it Layout.vue:

```
<template>
    <div class="theme-container">
        <Content/>
    </div>
</template>
```
## Create a Vuepress site

Go to your normal work area and generate a Vuepress site:

```bash
$ mkdir -p ~/code/vue/vuepress/baretest/.vuepress
$ cd ~/code/vue/vuepress/baretest
$ echo "# hello, world." > README.md
```
### Name theme in config.js

Create or update the file `./vuepress/config.js`:

```
$ vim .vuepress/config.js
```

Contents of `./vuepress/config.js`:

```
const base = process.env.GH ? '/vuepress/' : '/'
module.exports = {
    title: "Bare",
    description: "Minimal custom Vuepress theme",
    theme: "bare"
}
```

Generate the site and run the server:

```bash
$ vuepress build
```


### Location of theme directory (MacOS)

If your theme is named "bare", then you'll need a directory named
`/usr/local/lib/node_modules/vuepress-theme-bare`. It
will be referred to as `bare` in `/.vuepress/config.js`.




## Reference
* VuePress [Guide](https://vuepress.vuejs.org/guide/)
* [Source](https://github.com/vuejs/vuepress/tree/master/lib/default-theme) for default theme
  - [Layout.vue](https://github.com/vuejs/vuepress/blob/master/lib/default-theme/Layout.vue)
  - [Home.vue](https://github.com/vuejs/vuepress/blob/master/lib/default-theme/Home.vue)
* [Custom themes](https://vuepress.vuejs.org/guide/custom-themes.html)
* The "[simplest theme](https://vuepress.vuejs.org/guide/custom-themes.html#content-outlet)"
* [Custom layout for specific pages](https://vuepress.vuejs.org/default-theme-config/#custom-layout-for-specific-pages)
* Location of default theme files on MacOS: `/usr/local/lib/node_modules/vuepress/lib/default-theme/`
