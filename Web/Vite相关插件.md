# rollup-plugin-visualizer 打包体积分析插件

###### 安装

```bash
npm install --save-dev rollup-plugin-visualizer
# 或
yarn add -D rollup-plugin-visualizer
```

###### 配置

```ts
// vite.config 文件中配置
import { visualizer } from "rollup-plugin-visualizer";

export default defineConfig({
  plugins: [
    vue(),
    visualizer({
        open:true,  //注意这里要设置为true，否则无效
        gzipSize:true,
        brotliSize:true
    })
  ],
})

```

