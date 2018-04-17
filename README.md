# VuePress notes

Notes on creating a VuePress website from someone who loves VuePress but isn't an expert Vue or
static site developer.

## Creating a minimal custom theme

These notes begin by creating a custom theme from scratch. The general outline is:

* Create a directory in `/usr/local/lib/node_modules` with `vuepress-theme-` as a prefix for your theme name. In this example the base theme name is `starter1`.
* Create a minimal `Layout.vue` in that directory.
* Create a minimal `Home.vue` in the same directory with identical contents.
* Add the base theme name to your `config.js`

### Set up directories in /usr/local/lib/node_modules

Custom themes live in the directory /usr/local/lib/node_modules, so create it and change to that directory:

```bash
# Create a directory for the them under node_modules. 
$ sudo mkdir -p /usr/local/lib/node_modules/vuepress-theme-starter1

# Make it the working directory.
$ cd /usr/local/lib/node_modules/vuepress-theme-starter1
```

### Create the files Layout.vue and Home.vue

* Add this file to the theme directory and name it `Layout.vue`. Give it these contents:

```
<template> 
    <Content/> 
</template> 
```

* Create an identical file in the same directory and name it `Home.vue`. Give it the same contents:

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

Go to your normal work area and generate a Vuepress site. In this case
you would replace ~/code/vue/vuepress with wherever you choose to put
your Vuepress files. This site's directory is creatively called `demo1`.

```bash
# Create full directory path, including the
# necessary hidden directory .vuepress
$ mkdir -p ~/code/vue/vuepress/demo1/.vuepress

# Make it the working directory.
$ cd ~/code/vue/vuepress/demo1

# Create a minimal site, which includes nothing
# but a home page with a single h1 header.
$ echo "# hello, world." > README.md
```
### Name theme in config.js

Create the file `./vuepress/config.js`:

```
# Replace vim with your favorite editor 
$ vim .vuepress/config.js
```

Contents of `./vuepress/config.js`:

```
const base = process.env.GH ? '/vuepress/' : '/'
module.exports = {
    title: "Demo1",
    description: "Demo of starter1 custom Vuepress theme",
    theme: "starter1"
}
```

Generate the site and run the server:

```bash
$ vuepress build
```
And visit your site:

![Screen shot of the minimal VuePress theme named starter1 ](/img/starter1-vue-theme.png)

## Reference
* VuePress [Guide](https://vuepress.vuejs.org/guide/)
* [Source](https://github.com/vuejs/vuepress/tree/master/lib/default-theme) for default theme
  - [Layout.vue](https://github.com/vuejs/vuepress/blob/master/lib/default-theme/Layout.vue)
  - [Home.vue](https://github.com/vuejs/vuepress/blob/master/lib/default-theme/Home.vue)
* [Custom themes](https://vuepress.vuejs.org/guide/custom-themes.html)
* The "[simplest theme](https://vuepress.vuejs.org/guide/custom-themes.html#content-outlet)"
* [Custom layout for specific pages](https://vuepress.vuejs.org/default-theme-config/#custom-layout-for-specific-pages)
* Location of default theme files on MacOS: `/usr/local/lib/node_modules/vuepress/lib/default-theme/`
