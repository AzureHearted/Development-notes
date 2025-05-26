# 指令对比

下面针对一些常用的指令进行对比：

| 描述                                 | `yarn`                                                       | `npm`                                                        |
| ------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 初始化`package.json`                 | `yarn init` (可以在后面添加`-y`跳过询问的信息)               | `npm init` (可以在后面添加`-y`跳过询问的信息)                |
| 根据`package.json`安装依赖           | `yarn install`（可以省略install）                            | `npm install`(install可以缩写成`i`)                          |
| 安装某个依赖(默认是在`dependencies`) | `yarn add packageName --save`（简写`-S`，或者省略该参数）    | `npm install packageName --save`（简写`-S`，或者省略该参数） |
| 安装某个依赖在`devDependencies`      | `yarn add packageName --dev`（可以简写成`-D`）               | `npm install packageName --save-dev`（可以简写成`-D`）       |
| 全局安装依赖                         | `yarn global add packageName`                                | `npm install  packageName -g`                                |
| 移除依赖                             | `yarn remove packageName`                                    | `npm uninstall packageName`                                  |
| 移除全局依赖                         | `yarn global remove packageName`                             | `npm uninstall packageName -g`                               |
| 升级依赖                             | `yarn upgrade packageName`（如果是全局的依赖则在`yarn`后面加上`global`） | `npm update packageName`（如果是全局的依赖则在后面加上`-g`） |
| 查看依赖的信息                       | `yarn info packageName`                                      | `npm info packageName`                                       |
| 查看所有配置                         | `npm config list`                                            | `npm config list` 或者 `npm config ls -l`                    |
| 查看某个配置的信息                   | `yarn config get configName`                                 | `npm config get configName`                                  |
| 设置淘宝源                           | `yarn config set registry https://registry.npm.taobao.org`   | `npm config set registry https://registry.npm.taobao.org`    |
| 查看当前源                           | `yarn config get registry`                                   | `npm config get registry`                                    |
| 罗列全局依赖                         | `yarn global list --depth=0`                                 | `npm list -g --depth 0`                                      |
| 查看全局依赖目录                     | `yarn global bin` 或者`yarn global dir`                      | `npm prefix -g`                                              |
| 查看全局缓存的目录                   | `yarn cache dir`                                             | `npm config get cache`                                       |

