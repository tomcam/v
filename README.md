# VuePress notes

Notes on creating a VuePress website from someone who loves VuePress but isn't an expert Vue or
static site developer.

## Creating a minimal custom theme

These notes begin by creating a custom theme from scratch. The general outline is:

* Create a directory in `/usr/local/lib/node_modules` with `vuepress-theme-` as a prefix for your theme name. In this example the base theme name is `starter1`.
* Create a minimal `Layout.vue` in that directory.
* Add the base theme name to your `config.js`

### Set up directories in /usr/local/lib/node_modules

Custom themes live in the directory /usr/local/lib/node_modules, so create it and change to that directory:

```bash
# This creates a full directory tree including
# the necessary hidden .vuepress directory 
$ sudo mkdir -p /usr/local/lib/node_modules/vuepress-theme-starter1/.vuepress
# Make it the working directory.
$ cd /usr/local/lib/node_modules/vuepress-theme-starter1
```

### Create the file Layout.vue

Add this file to the theme directory and name it `Layout.vue`.
The minimal `Layout.vue` looks like this:

```
<template> 
    <Content/> 
</template> 
```

<!--
This is the minimal version that was accepted--but no output appeared.

```
<template>
  <div class="theme-container">
    <h1>This is Layout.vue</h1>
    <Content/>
    <h1>This came under the content tag</h1>
  </div>
</template>

<script>
import Vue from 'vue'
export default {
  components: { Home, Page, Sidebar, Navbar },
  data () {
    return {
      isSidebarOpen: false
    }
  }
}

</script>
```
-->

## Create a Vuepress site

Go to your normal work area and generate a Vuepress site:

```bash
$ mkdir -p ~/code/vue/vuepress/starter1/.vuepress
$ cd ~/code/vue/vuepress/starter1
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
    title: "Starter1",
    description: "Minimal custom Vuepress theme",
    theme: "starter1"
}
```

Generate the site and run the server:

```bash
$ vuepress build
```

### Location of theme directory (MacOS)

If your theme is named "starter1", then you'll need a directory named
`/usr/local/lib/node_modules/vuepress-theme-starter1`. It
will be referred to as `starter1` in `/.vuepress/config.js`.


## Reference
* VuePress [Guide](https://vuepress.vuejs.org/guide/)
* [Source](https://github.com/vuejs/vuepress/tree/master/lib/default-theme) for default theme
  - [Layout.vue](https://github.com/vuejs/vuepress/blob/master/lib/default-theme/Layout.vue)
  - [Home.vue](https://github.com/vuejs/vuepress/blob/master/lib/default-theme/Home.vue)
* [Custom themes](https://vuepress.vuejs.org/guide/custom-themes.html)
* The "[simplest theme](https://vuepress.vuejs.org/guide/custom-themes.html#content-outlet)"
* [Custom layout for specific pages](https://vuepress.vuejs.org/default-theme-config/#custom-layout-for-specific-pages)
* Location of default theme files on MacOS: `/usr/local/lib/node_modules/vuepress/lib/default-theme/`
