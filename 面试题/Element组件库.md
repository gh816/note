# Element组件库

https://element-plus.org/ element-plus中文网

1.安装

npm insatll element-plus  --save

2.整体导入 ElementPlus 组件库

import ElementPlus from 'element-plus'

import 'element-plus/dist/index.css'

3.如何简单使用ui组件库

比如要使用button，我一般是去element官网去查看button相关的内容，那里面会有button相关样式的写法

```
<el-row>
  <el-button round>圆角按钮</el-button>
  <el-button type="primary" round color="green">主要按钮</el-button>
  <el-button type="success" round>成功按钮</el-button>
  <el-button type="info" circle>信息按钮</el-button>
  <el-button type="warning" round size="small">警告按钮</el-button>
  <el-button type="danger" loading size="large">加载中</el-button>
</el-row>
```

这里的type就是按钮的类型，不同的type会显示不同的样式

这里的size就是指定按钮大小

然后组件中的round和loading是组件属性，round表示边框是圆角，loading表示加载中的

color属性表示可以定义按钮的颜色

## 使用icon图标

1.npm install @element-plus/icons-vue安装包管理

2.*导入ElementPlus 组件库中所有图标*

import * as ElementPlusIconsVue from '@element-plus/icons-vue'

3.*注册ElementPlus组件库中的所有图标到全局Vue应用的*

```
for (const [key, component] of Object.entries(ElementPlusIconsVue)) {
  app.component(key, component)
}
```

### 基本用法

```
<template>
  <el-button type="primary" color="#ccc">
    <el-icon>
      <Search />
    </el-icon>
  <span>搜索</span>
  </el-button>
</template>
```

1.<el-icon></el-icon>用于显示图标的组件，可以通过设置不同的属性来控制图标大小和颜色

2<Edit/>是表示一个编辑图标

3.图标可以结合button按钮使用

## 提示框

```
<template>
  <el-button plain="true" @click="open">Success</el-button>
</template>

<script>
import { ElMessage  } from 'element-plus'
export default {
  setup() {
    const open = () => {
      ElMessage({
        message: 'this is a success message.',
        type: 'success',
        offset: 200,
        showClose: true
      })
    }
    return { open }
  }
}
</script>
```

1.使用提示框要先引入

2.还要绑定一个方法来触发提示框

3.方法里面会有一个ElMessage()函数，函数里面接收一个对象，对象里面可以接收一下属性，比如message就是提示框的信息，

然后type就是提示框的类型，有成功，失败，警告等，具体文档都有。