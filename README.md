# v
VuePress notes

## Creating a minimal custom theme

### Name theme in config.js

Create or update the file ./vuepress/config.js:

```
const base = process.env.GH ? '/vuepress/' : '/'
module.exports = {
    title: "Bare",
    description: "Minimal custom Vuepress theme",
    theme: "bare"
}
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
