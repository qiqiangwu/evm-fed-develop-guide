<!-- vscode-markdown-toc -->

- 1. [术语](#术语)
  - 1.1. [命名规范](#命名规范)
  - 1.2. [文件类型](#文件类型)
  - 1.3. [可创建目录类型](#可创建目录类型)
- 2. [命名](#命名)
  - 2.1. [文件夹命名](#文件夹命名)
  - 2.2. [文件命名](#文件命名)
  - 2.3. [标识符命名](#标识符命名)
- 3. [目录结构](#目录结构)
  - 3.1. [index.ts](#index.ts)
  - 3.2. [创建目录和文件](#创建目录和文件)
- 4. [svn 忽略文件](#svn-忽略文件)

<!-- vscode-markdown-toc-config
	numbering=true
	autoSave=true
	/vscode-markdown-toc-config -->
<!-- /vscode-markdown-toc -->

# React Native 开发指南

## 1. <a name='术语'></a>术语

### 1.1. <a name='命名规范'></a>命名规范

常见命名规范，分为以下几种：

- kebab-case：短横线单词连接命名法，单词全部小写，用短横线连接，例如：login-account
- camelCase：驼峰命名法，第一个单词首字母小写，第二个单词首字母大写，例如：firstName
- PascalCase：帕斯卡命名法（俗称大驼峰命名法），每个单词首字母大写，例如：FirstName
- under_score_case：下划线命名法

### 1.2. <a name='文件类型'></a>文件类型

- helper 一般针对特定项目的辅助函数，通用性不及 util
- util 通用工具函数
- hook react hook
- type 类型定义
- service 服务
- model 服务数据类型
- dao 用于 Realm 数据访问文件
- schema 用于定义 Realm 数据格式文件

### 1.3. <a name='可创建目录类型'></a>可创建目录类型

- components - react 组件文件，可用于公共组件或者页面目录下
- assets - 资源文件，可以参考具体使用方式建立
- slices - redux slice 文件，一般建立在页面或 redux 目录下

## 2. <a name='命名'></a>命名

### 2.1. <a name='文件夹命名'></a>文件夹命名

文件夹命名采用 kebab-case 命名法

### 2.2. <a name='文件命名'></a>文件命名

React 组件文件命名采用 PascalCase 命名法，其他文件采用 kebab-case 命名法

**建议**非 React 组件文件命名可带[文件类型](#文件类型)扩展，如果父文件夹名称可以描述文件类型，子文件命名可以不带文件类型扩展，例如：get-random-number.util.ts

类型文件夹采用复数形式，例如：components、assets、slices 等

### 2.3. <a name='标识符命名'></a>标识符命名

- 常量命名  
  全部大写，多个单词用下划线连接
  例如：AREA_TYPES
- 变量  
  使用 CamelCase 命名法
- 属性  
  使用 CamelCase 命名法

### react 组件

使用 PascalCase 命名法

- 页面组件命名  
  添加 Screen 后缀  
  例子：
  ```
  const AddFriendScreen = ()=>{}
  export default AddFriendScreen
  ```
- modal 组件命名
  添加 Modal 后缀  
  例子：
  ```
  const AudioSettingModal = ()=>{}
  export default AudioSettingModal
  ```

### redux 命名

- state 接口命名  
  特性名称+State 后缀
- 初始状态变量  
  统一使用 initialState 变量名
- slice 变量名称
  特性名称+Slice 后缀
- slice name
  特性名称 CamelCase 命名法
- action
  非导出 action  
  直接有 slice.actions 结构  
  导出 action  
  非导出 action+Action 后缀
- thunk 变量命名  
  特性名称+Thunk 后缀
- thunk typePrefix
  同 thunk 变量名称
- slice reducer 变量名称
  特性名称+Reducer 后缀  
  先定义 reducer 变量，然后默认导出
- store reducer 属性名  
  特性名称，例如：appData、user

注：特性名称命名参考变量或属性命名

例子：

```
// src/redux/slices/app-data.slice.ts
// state 接口
interface AppDataState{
  ...
}
// 初始状态变量
const initialState: AppDataState = {
  isFirstInstall: true,
};
// slice 变量名称
const appDataSlice = createSlice({
  // slice name
  name: 'appData'
});

// actions
// 非导出actions
const {setIsFirstInstall} = appDataSlice.actions;
// 导出actions
export const setIsFirstInstallAction = setIsFirstInstall;

// thunk变量命名
// thunk
export const getAppDataThunk = createAsyncThunk<void, void, {dispatch: AppDispatch}>(
    // thunk typePrefix
    'getAppDataThunk',
    async (_, {dispatch}) => {
      ...
    });
// slice reducer 变量名称
// reducer
const appDataReducer = appDataSlice.reducer;
export default appDataReducer;
```

### 导航

- 路由名称  
  路由名称采用下划线命名法，例如：bottom_tab，change_user_name，login
- 页面属性命名  
  页面组件名称+Prop 后缀
  例子：

  ```
  // src/navigation/navigation.type.ts
  export type LoginScreenProp = NativeStackScreenProps<RootParamList, 'login'>;
  ```

## 3. <a name='目录结构'></a>目录结构

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

### 3.1. <a name='index.ts'></a>index.ts

**强制**禁止使用 index.ts

### 3.2. <a name='创建目录和文件'></a>创建目录和文件

- src/screens 页面目录  
   **建议**按照页面类型建立子目录  
   页面子目录可以包含 components、slices、assets 和特性文件夹

  例子：

  ```
  add-friend - 添加好友页面目录
  ├─AddFriend.tsx - 添加好友首页组件
  ├─by-account - 特性文件夹，表示通过用户账号添加好友页面
  |     ├─ByAccount.tsx
  |     ├─slices - 添加好友页面redux slice
  |     |   ├─apply-friend.slice.ts
  |     |   └search-user-by-phone.slice.ts
  ├─assets - 添加好友资源目录
  |   ├─navigation_add_maillist.png
  |   └navigation_add_search.png
  ```

## 4. <a name='svn-忽略文件'></a>svn 忽略文件
