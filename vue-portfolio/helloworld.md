# vue-portfolio

## Intro

`vue-portfolio` 是我为了学习 `vuejs` 而做的一个项目，主要是为了学习 `vuejs` 的基本用法。`vue-porfolio` 是一个个人网站，我会在这个网站上展示我自己的一些信息，比如我的个人信息，我的项目经历，我的技能等等。

## 功能
### 以树状图的形式展示我的工作经验
通过CSS可以很容易的实现树状图的形式
1. 做树状图的第一步就是先做树干

这里我使用伪元素 `:before`来实现，好处在于伪元素的高度可以自适应，不需要额外设置高度

```css
.timeline:before {
  content: "";
  position: absolute;
  top: 0;
  bottom: 0;
  left: 50%;
  width: 2px;
  background-color: #34495e;
}
```
2. 做树枝

做完树干之后我们就可以做树枝了,树枝的实现也很简单，使用`<li>`的伪元素`::before`来实现

只有树枝会显得很单调，我们可以再树枝末端加上一个小圆点当作树叶修饰一下，
树叶通过伪元素`::after`来实现

```css

/* 树叶/leaf */
.timeline li:before {
  content: "";
  position: absolute;
  top: 5px;
  width: 20px;
  height: 20px;
  border-radius: 50%;
  background-color: #fff;
  border: 2px solid #34495e;
  z-index: 2;
}

/* 树枝/branch  */
.timeline li:after {
  content: "";
  position: absolute;
  top: 15px;
  width: 30%;
  height: 2px;
  background-color: #34495e;
}

```

## 技术栈

## i18n

i18n 代表 internationalization，即国际化，多语言功能。在这个项目中，我使用了 `vue-i18n` 来实现 i18n。`vue-i18n` 的使用非常简单，只需要在 `main.js` 中引入 `vue-i18n`，然后在 `main.js` 中配置 `vue-i18n`，就可以在项目中使用 `vue-i18n` 了。

实现 i8n 的步骤遇到一点问题，在改变 locale 的时候，我注意到不是所有的 component locale 都发生了改变，原因是因为在 `data()` 中定义的变量没有及时更新.

解决方法有两种:

1. 在 `data()` 中定义的变量改为 `computed` （Credits to [StackOverflow](https://stackoverflow.com/questions/50278554/vue-i18n-not-updating-when-changing-locale)）

```js
// 在data中定义的变量不会及时更新
data() {
    return {
      title: this.$t("sectionTitles.skills"),
    };
  },
```

```js
// 在computed中定义的变量会及时更新
computed: {
    title() {
      return this.$t("sectionTitles.skills");
    },
  },
```

2. 把 `data()` 中定义的变量直接放到 `template` 中

```html
<h1>{{ $t("greeting") }}</h1>
```
