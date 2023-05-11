# vue-portfolio

## Intro

`vue-portfolio` 是我为了学习 `vuejs` 而做的一个项目，主要是为了学习 `vuejs` 的基本用法。`vue-porfolio` 是一个个人网站，我会在这个网站上展示我自己的一些信息，比如我的个人信息，我的项目经历，我的技能等等。

## 技术栈

## i18n

i18n 代表 internationalization，即国际化，多语言功能。在这个项目中，我使用了 `vue-i18n` 来实现 i18n。`vue-i18n` 的使用非常简单，只需要在 `main.js` 中引入 `vue-i18n`，然后在 `main.js` 中配置 `vue-i18n`，就可以在项目中使用 `vue-i18n` 了。

实现 i8n 的步骤遇到一点问题，在改变 locale 的时候，我注意到不是所有的 component locale 都发生了改变，原因是因为在 `data()` 中定义的变量没有及时更新,
解决方法有两种

- 在 `data()` 中定义的变量改为 `computed`

```js
// 在data中定义变量不会及时更新
data() {
    return {
      title: this.$t("sectionTitles.skills"),
    };
  },
```

```js
// 在computed中定义变量会及时更新
computed: {
    title() {
      return this.$t("sectionTitles.skills");
    },
  },
```

- 把 `data()` 中定义的变量直接放到 `template` 中

```html
<h1>{{ $t("greeting") }}</h1>
```
