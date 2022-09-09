# effect



[![lerna](https://img.shields.io/badge/maintained%20with-lerna-cc00ff.svg)](https://lerna.js.org/)

## Getting started

```sh
$ npm i -g lerna # >= 3.19.0
$ npm i -g yarn@1 # <= 2.0.0
```

```sh
# install all dependencies
$ yarn

# create a config file
$ cd packages/<package-name>
$ formula config # select `formula.config|h5-app.js`

# running specified package
$ formula dev -d packages/<package-name>
```

## How to develop

### Create a new package

```sh
$ lerna create <package-name>

$ cd <path-to-package-name>

# each package should has it's own config file
$ formula config # select `formula.config|h5-app.js`
```

🌟**NOTICE:**

Please keep in mind when created a new package, DO NOT FORGET to specify the `category` field into package.json. It's important for deploy stage in CI pipeline when to build app resources.

```json
{
  "category": "vue-app",
}
```

### Develop

In order to let CI known which package to build, it is required to specify `<package-name>` in branch name

```sh
# branch pattern: `<package-name>/<feature-name>`

$ git checkout -b <package-name>/add-new-feature
```

We have a package named `shared` to shared some logic and files cross packages,
you can \`install\` this package as dependency like usual by using `lerna add` command

```sh
$ cd <path-to-package-name>

$ lerna add shared
```

After linking `shared` library, you can use it in package like following:

```js
import setup from 'shared/setup'
```

### Release

```sh
$ git checkout master
$ git add .
$ git commit -m 'feat: initial commit'

# before running the following command
# ensure that working directory is clean
$ lerna version
```

## ReDS 基础组件
https://fe-docs.devops.xiaohongshu.com/reds-web/guide/start

## Onix 组件市场
https://fe-docs.devops.xiaohongshu.com/onix/onix-readme# vue3----
