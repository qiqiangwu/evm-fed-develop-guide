# SVN 使用规范

## 创建目录

目录命名采用短横线单词连接命名法，例如：rn-evm-player

例子：

```
rn-evm-player
├─branches - 分支目录
├─tags - tag目录
├─trunk - 主版本目录
```

**trunk 下直接放置代码**

## SVN 工作流

1. 开发时创建开发分支到 branches 下，开发完成，更新 trunk 到当前开发分支完成测试，然后提交并合并到 trunk 分支
2. 发布版本，建立 tag 版本到 tags 下
3. 不建议直接 trunk 分支下开发

## svn 忽略文件

### React Native Custom Module
