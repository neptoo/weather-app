# weather-app



## 推荐插件
- [Tailwind CSS IntelliSense](https://marketplace.visualstudio.com/items?itemName=bradlc.vscode-tailwindcss)
- [Vue VSCode Snippets](https://marketplace.visualstudio.com/items?itemName=sdras.vue-vscode-snippets)
- [Vue (Official)](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur).


## 项目启动和配置

```sh
npm install
```

```sh
npm run dev
```

```sh
npm run build
```

### 在vue3项目中使用tailwind4

```bash
npm install tailwindcss @tailwindcss/vite
```

配置vite.config.js

```js
import { defineConfig } from 'vite'
import tailwindcss from '@tailwindcss/vite'  // 这一行

export default defineConfig({
  plugins: [
    tailwindcss(),  // 和这一行
  ],
})
```

在CSS文件中引入

```css
/* index.css */
@import "tailwindcss";
```

在main.js中引入CSS文件

```js
import './index.css'
```

### 在tailwind中自定义颜色

```css
@import "tailwindcss";

@theme {
  --color-primary: #00668A;
  --color-midnight: #121063;
}
```

然后你就可以在项目中通过`bg-primary`或者`text-midnight`使用自定义的颜色



