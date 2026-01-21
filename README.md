# 宫崎骏动漫官网
## 一、项目启动方式和说明
        本项目由多人协作开发，使用Git管理代码和仓库，使用Vue框架将功能组件化，为呈现项目的开发过程，采用了多次提交创建多个功能分支并合并到主分支的提交方式，并以feature/**的方式命名，由于不同同学负责不同的内容，因此分支内容只代表相应的功能实现，并不为完整的项目实现，完整的项目为main分支的内容。
        项目地址：https://github.com/paradise611/homework.git
        启动方式：克隆仓库中的main分支中的项目
        访问网站：https://y56cy.github.io/homework/
```bash
git clone https://github.com/paradise611/homework.git
```



## 二、选题背景与项目介绍
        宫崎骏动漫系列凭借细腻的叙事与治愈的视觉风格，收获了全球广大群体的喜爱与追捧，出于对其动漫作品和喜爱，以及对宫崎骏先生的敬意，我们选择宫崎骏动漫官网作为作业项目，旨在对宫崎骏多年来的作品做一个总结和介绍，一切资源均来源于网络。

	    该项目分为个不同的页面:首页、作品一览、作者介绍、精美图片、精彩二创、相关资讯，包含丰富的交互元素与视觉呈现形式，比如动态轮播的作品海报、响应式的资讯布局、沉浸式的图片展示模块、飘落的樱花粒子等；综合使用HTML实现多种功能和结构搭建，使用vue框架将页面组件化，清晰地展现了页面结构，同时使用丰富的css美化样式，具有艺术与技术双重价值。

## 三、小组分工
        本项目由赵紫涵、王若欣、杨彩艺、崔蔚恩四人共同完成，项目分为不同的页面部分，进行了较为明确的分工合作，每个人负责不同的页面和功能，并最后汇总修改。在创作过程中，每个人都提出了自己见解和建议，遇到问题积极讨论并且一同解决，不断完善项目，最终呈现出一个很好的效果，使整个项目风格一致的同时保持了各自的特色。
-	赵紫涵：提出项目灵感作出项目计划，主要负责works.vue页面的实现以及导航栏和樱花粒子飘落效果的制作，以及项目报告，readme文件的撰写。
- 	杨彩艺：主要负责FunCreation.vue、PicturesPage.vue和RelatedinfoPage.vue三个页面的制作，和搜查图片、视频、资讯等资料，海报的制作。
- 王若欣：主要负责author.vue页面的制作，homepage.vue页面的框架构建，页脚的制作和视频的录制。
-	崔蔚恩：主要负责homepage.vue页面内容的填充，首页轮播图的制作，路由的实现以及提交到GitHub仓库。
- 	以及各自负责自己功能页面的代码提交和报告功能模块书写。
## 四、技术架构
        该项目使用Vue3框架构建，综合运用了HTML结构搭建、CSS样式美化、JavaScript交互实现以及Vue3框架的组件化开发思想，使用Vue Router实现页面跳转，将各个功能组件化并最后组成一个完整的页面；多人协作开发，使用Git管理代码，分别创建自己的功能分支，最终合并到主分支成为一个完整的项 目，避免代码冲突。
## 五、模块功能与功能实现
- **src/assets/css/variables.css:** 二创页面的样式文件，通过全局变量控制 --border-radius等参数。
- **src/assets/images：** 项目所需的图片文件
- **src/router/index.js：** 路由的实现所需的文件，实现页面间跳转
- **src/App.vue：** Vue项目的根组件，整个项目的入口文件
- **src/Author.vue：** 作者页面的实现
- **src/FunCreation.vue：** 精彩二创页面的实现
- **src/Homepage.vue：** 首页页面的实现
- **src/PicturesPage.vue：** 精美图片页面的实现
- **src/RelatedinfoPage.vue：** 相关资讯页面的实现
- **src/works.vue：** 作品一览页面的实现
- **src/components/Nav.vue&src/components/Sakura.vue&src/components/allfooter.vue：** 公共页面组件，分别为导航栏，粒子飘落效果和页脚
- **src/components/home_com：** 首页页面所使用的组件
- **src/components/Author_com：** 作者页面所使用的组件
- **src/components/PictureRelated：** 精美图片页面所使用的组件
- **src/components/Relatedinfo：** 相关资讯页面所使用的组件
- **src/components/movies.vue&src/components/headphoto.vue：** 作品页面所使用的组件

