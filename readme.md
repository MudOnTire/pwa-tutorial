# PWA入门详解

![image](http://lc-jOYHMCEn.cn-n1.lcfile.com/7348400570d1df39842a/pwa.png)

# 简介

前端的同学是否曾想过学习app开发，以弥补自己移动端能力的不足？在面对一众的选择时是否略显迷茫？是学习ios还是android开发？是学习原生开发、混合开发（[Ionic](https://ionicframework.com/)，还是使用[react native](https://facebook.github.io/react-native/)或者[flutter](https://flutter.dev/)这样的跨平台框架？而app开发的学习周期长、学习成本高也让很多一部分人望而却步。得益于前端技术的飞速发展、浏览器性能的不断提高，使用网页技术开发出接近原生体验的应用得以变为现实，PWA就在这样的背景下应运而生。可以用自己熟悉的HTML、CSS、Javascript开发出媲美原生app的网站，不仅拥有接近原生app的流畅程度，并且具备原生app才有的特性，比如：a. 可以在主屏上安装应用图标，b. 离线状态下访问，c. 获取消息通知，等等。。PWA的出现让大家看到了希望！

# 与原生应用对比

那PWA和原生应用相比到底有何竞争力呢？我们分别看一下原生应用和PWA的特点：

**原生应用**

* 使用原生SDK和开发工具开发
* 需要考虑跨平台，不同系统往往需要独立开发
* 需要发布到应用商店才能下载使用
* 可以安装到手机主屏，生成应用图标
* 直接运行于操作系统上，访问系统资源方便
* 可以离线使用
* 可以获取消息通知

**PWA应用**

* 使用HTML，CSS，JS开发
* 无需考虑跨平台，只需要考虑浏览器兼容性
* 通过url访问，无需发布到应用商店
* 可以安装到手机主屏，生成应用图标
* 运行于浏览器中，可访问系统资源
* 可以离线使用
* 可以获取消息通知

可以发现PWA具备了原生应用的主要能力，但是开发流程却比原生应用更加简洁：a. html/css/js的群众基础更好，开发效率更高；b. 省去了为不同系统开发独立版本的大量成本；c. 省去了上架到应用市场的繁琐流程；d. 无需前往应用商店下载，用户使用起来也更加方便。但是值得注意的是，PWA还是相对比较新的技术，规范还有很多调整的空间，很多浏览器对PWA的支持也还不完善，但是PWA是一个趋势，所以现在学习正合适！

本文将通过一个简单的列子像大家展示PWA的开发流程。完成后的列子是 [这样]() 的。

# 创建项目

项目使用Vue + Ionic的组合进行开发。

1. 首先全局安装 `@vue/cli`：

```
npm install -g @vue/cli
```

2. 初始化vue项目：

```
vue create vue-ionic-pwa
```

3. 安装 `vue-router`，因为ionic的路由依赖于`vue-router`：

```
vue add router
```

4. 安装 `@ionic/vue`

```
npm install @ionic/vue
```

5. 在 `src/main.js` 中添加对ionic的引用：

```
...
import Ionic from '@ionic/vue'
import '@ionic/core/css/ionic.bundle.css'

Vue.use(Ionic)
...
```

6. 在 `src/router.js` 中使用 `IonicVueRouter` 替换默认的vue router：

```
import Vue from 'vue'
import { IonicVueRouter } from '@ionic/vue';
import Home from './views/Home.vue'

Vue.use(IonicVueRouter)

export default new IonicVueRouter({
  mode: 'history',
  base: process.env.BASE_URL,
  routes: [
    {
      path: '/',
      name: 'home',
      component: Home
    }
  ]
})
```

7. 将 `src/App.vue` 内容修改为：

```
<template>
  <div id="app">
    <ion-app>
      <ion-vue-router/>
    </ion-app>
  </div>
</template>
```

8. 将 `src/views/Home.vue` 内容修改为：

```
<template>
  <div class="ion-page">
    <ion-header>
      <ion-toolbar>
        <ion-title>
          ZipInfo
        </ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content class="ion-padding">My App</ion-content>
  </div>
</template>

<script>
export default {
  name: 'home',
  components: {}
}
</script>
```

最后，我们运行`yarn serve`看下效果：

![1](http://lc-jOYHMCEn.cn-n1.lcfile.com/63ae4b1e9d2926ece165/Screen%20Shot%202019-06-06%20at%2011.58.36%20AM.png)