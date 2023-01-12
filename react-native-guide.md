# React Native 开发指南

## 术语

### 命名规范

常见命名规范，分为以下几种：

- kebab-case：短横线单词连接命名法，单词全部小写，用短横线连接，例如：login-account
- camelCase：驼峰命名法，第一个单词首字母小写，第二个单词首字母大写，例如：firstName
- PascalCase：帕斯卡命名法（俗称大驼峰命名法），每个单词首字母大写，例如：FirstName

### 文件类型

- helper 一般针对特定项目的辅助函数，通用性不及 util
- util 通用工具函数
- hook react hook
- type 类型定义
- service 服务
- model 服务数据类型
- dao 用于 Realm 数据访问文件
- schema 用于定义 Realm 数据格式文件

### 可创建目录类型

- components - 组件文件，可用于公共组件或者页面目录下
- assets - 资源文件，可以参考具体使用方式建立
- slices - redux slice 文件，一般建立在页面或 redux 目录下

## 命名

### 文件夹命名

文件夹命名采用 kebab-case 命名法

### 文件命名

React 组件文件命名采用 PascalCase 命名法，其他文件采用 kebab-case 命名法

**建议**非 React 组件文件命名可带[文件类型](#文件类型)扩展，如果父文件夹名称可以描述文件类型，子文件命名可以不带文件类型扩展，例如：get-random-number.util.ts

类型文件夹采用复数形式，例如：components、assets、slices 等

### 标识符命名

- 常量命名  
  全部大写，多个单词用下划线连接
  例如：AREA_TYPES
- 变量  
  使用 CamelCase 命名法

## 目录结构

```
video_meeting_public
├─README.md
├─index.js - 项目入口文件
├─package.json - node配置文件
├─android - android原生文件目录
├─ios - ios原生文件目录
├─doc - 项目相关文档目录
├─src - JS源代码目录
| ├─App.tsx - App组件
| ├─screens - 页面文件目录
| ├─redux - redux目录
| | ├─AppStore.tsx - redux store
| | ├─slices - redux slice目录，一般可共用
| ├─navigation - 导航目录
| | ├─Navigation.tsx - 导航组件
| | ├─navigation.helper.ts - 导航辅助函数文件
| | ├─navigation.type.ts - 导航类型文件
| ├─modals - modal页面目录
| ├─data - 访问远程数据和本地数据目录
| | ├─repository.ts - 数据访问入口文件
| | ├─repository.type.ts - 数据访问类型文件
| | ├─remote - 访问远程数据目录
| | | ├─mappers.ts
| | | ├─request-gateway.ts
| | | ├─types
| | | ├─services
| | | ├─models
| | ├─local - 访问本地数据目录
| | | ├─database.ts
| | | ├─schema-map.ts
| | | ├─schema-name.ts
| | | ├─schemas
| | | ├─daos
| ├─common - 公共资源目录
| | ├─constants.ts - 应用常量定义文件
| | ├─utils - 通用工具函数目录
| | ├─types - 类型目录
| | ├─theme - 风格目录
| | ├─modules - 自定义RN组件目录
| | ├─layouts - 布局目录
| | ├─hooks - react hooks目录
| | ├─helpers - 项目级辅助函数目录
| | ├─components - 公共组件目录
| | ├─assets - 公共资源目录
├─assets - 原生资源目录
| ├─fonts - 字体目录
├─__tests__ - 测试代码目录
```

### 创建目录和文件

- src/screens 页面目录  
  按照页面建立子目录  
  页面子目录可以包含 components、slices、assets
