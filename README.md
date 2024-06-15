# ts-lib-template

一个 ts lib 的模板仓库，可以当做初始化 ts 库使用。

- [ ] 1. 支持单元测试与覆盖率统计
- [ ] 2. 使用 standard-version 或者 github action 升级版本号，产生 changelog
- [x] 3. tsup: 作为 TypeScript 库打包的最简单和最快的方法。
- [ ] 4. conventional commit 的校验支持
- [x] 5. Eslint + Prettier: 代码美化与语法检查的支持，以及相应的 git hooks 自动化支持

## 开发之前

1. 修改`package.json`的模块信息，模块名、作者和描述。
2. 删除 CHANGELOG.md
3. 修改 README.md

### 非 github 项目

使用 standard-version 来升级版本号，然后需要手动发布。

1. 删除.github 目录
2. 删除 doc:publish 命令
3. 删除 gh-pages 依赖包

### github 项目

使用 github action 自动化发布

1. 删除 npm version 命令
2. 删除 standard-version 依赖包
3. 在 github 项目配置 secrets：key 为 NPM_TOKEN，value 为 npm 的 token
4. 修改 github workflows 里面的 package-name（改成和 package.json 的 name 一样）
5. 在 github 仓库到 `Settings > Code and automation > Actions > General` > Workflow permissions， 打开 `Allow GitHub Actions to create and approve pull requests`.

### 最后

1. 安装依赖

## 开发与发布

### 开发

```shell
# 有变化就重新编译
npm run dev
```

### 发布

github 项目：

只要遵循 conventional commit 约定的提交，push 到 github 之后，会自动产生 merge request，合并之后就会自动发布

非 github 项目：

```shell
# 会先执行bumpp命令来管理版本号，并更新相关信息，然后执行npm publish命令将软件包发布到npm
npm run release
# 推送标签和代码
git push --follow-tags origin main
```

## 参考仓库

1. https://github.com/bitjson/typescript-starter
