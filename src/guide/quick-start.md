---
footer: false
---

<!-- # Quick Start -->

# Bắt đầu

Tùy thuộc vào trường hợp bạn sử dụng và sở thích của bạn, bạn có thể sử dụng Vue bằng cách sử dụng công cụ để tạo dự án hoặc dùng dường dẫn thư viện trực tiếp.

## Sử dụng công cụ hỗ trợ để tạo dự án

Là một công cụ cho phép xây dựng dự án bằng Vue dưới dạng [Single-File Component](/guide/scaling-up/sfc) (SFC). Công cụ xây dựng dự án bằng Vue dựa trên [Vite](https://vitejs.dev) - một công cụ xây dựng dự án web ở phía người dùng hiện đại, nhẹ nhàng và cực kỳ nhanh chóng.

### Trực tuyến

Bạn có thể thử tạo dự án Vue với dạng SFCs trực tuyến tại [StackBlitz](https://vite.new/vue). StackBlitz sẽ xây dựng những thiết Vite-based trực tiếp trên trình duyệt, vì vậy nó gần giống như bạn thực hiện trên máy tính mình mà không cần phải cài đặt thêm bất cứ gì.
### Local (Máy tính cá nhân)

:::tip Diều kiện tiên quyết

- Đã quen với việc sử dụng cửa sổ dòng lệnh
- Đã cài đặt [Node.js](https://nodejs.org/)
  :::

Để khởi tạo một dự án bằng Vue trên máy tính của bạn, vui lòng nhập dòng lệnh phía dưới (không có dấu `>` ở phía trước câu lệnh):


<div class="language-sh"><pre><code><span class="line"><span style="color:var(--vt-c-green);">&gt;</span> <span style="color:#A6ACCD;">npm init vue@latest</span></span></code></pre></div>

Lệnh này sẽ cài đặt và thực thi lệnh [create-vue](https://github.com/vuejs/create-vue) - một công cụ để tạo khuôn mẫu thư mục chính thức cho dự án sử dụng Vue. Bạn sẽ được giới thiệu một vài tính năng cơ bản cho dự án như dùng TypeScript hoặc hỗ trợ tesing (kiểm tra lỗi):

<div class="language-sh"><pre><code><span style="color:var(--vt-c-green);">✔</span> <span style="color:#A6ACCD;">Tên dự án: <span style="color:#888;">… <span style="color:#89DDFF;">&lt;</span><span style="color:#888;">tên-dự-án-của-bạn</span><span style="color:#89DDFF;">&gt;</span></span></span>
<span style="color:var(--vt-c-green);">✔</span> <span style="color:#A6ACCD;">Sử dụng TypeScript? <span style="color:#888;">… <span style="color:#89DDFF;text-decoration:underline">Không</span> / Có</span></span>
<span style="color:var(--vt-c-green);">✔</span> <span style="color:#A6ACCD;">Sử dụng JSX? <span style="color:#888;">… <span style="color:#89DDFF;text-decoration:underline">Không</span> / Có</span></span>
<span style="color:var(--vt-c-green);">✔</span> <span style="color:#A6ACCD;">Sử dụng Vue Router cho việc phát triển web dưới dạng Single Page Application development? <span style="color:#888;">… <span style="color:#89DDFF;text-decoration:underline">Không</span> / Có</span></span>
<span style="color:var(--vt-c-green);">✔</span> <span style="color:#A6ACCD;">Sử dụng Pinia để quản lý State? <span style="color:#888;">… <span style="color:#89DDFF;text-decoration:underline">No</span> / Yes</span></span>
<span style="color:var(--vt-c-green);">✔</span> <span style="color:#A6ACCD;">Sử dụng Cypress để testing? <span style="color:#888;">… <span style="color:#89DDFF;text-decoration:underline">No</span> / Yes</span></span>
<span></span>
<span style="color:#A6ACCD;">Tạo khuôn mẫu dự án trong ./<span style="color:#89DDFF;">&lt;</span><span style="color:#888;">tên-dự-án-của-bạn</span><span style="color:#89DDFF;">&gt;</span>...</span>
<span style="color:#A6ACCD;">Hoàn thành.</span></code></pre></div>

Nếu bạn không chắc chắn về một tùy chọn nào đó, đơn giản bạn nên chọn `Không` bằng cách nhấn phím `Enter` ngay bây giờ. Một khi dự án đã được tạo xong, vui lòng làm theo hướng dẫn phía dưới để cài những dêpndencies cần thiết và chạy dự án trên dev server (môi trường phát triển):

<div class="language-sh"><pre><code><span class="line"><span style="color:var(--vt-c-green);">&gt; </span><span style="color:#A6ACCD;">cd</span><span style="color:#A6ACCD;"> </span><span style="color:#89DDFF;">&lt;</span><span style="color:#888;">your-project-name</span><span style="color:#89DDFF;">&gt;</span></span>
<span class="line"><span style="color:var(--vt-c-green);">&gt; </span><span style="color:#A6ACCD;">npm install</span></span>
<span class="line"><span style="color:var(--vt-c-green);">&gt; </span><span style="color:#A6ACCD;">npm run dev</span></span>
<span class="line"></span></code></pre></div>

You should now have your first Vue project running! Here are some additional tips:
Bây giờ bạn đã có một dự án Vue đầu tiên đang chạy! Dưới đây là một vài mẹo khi xây dựng dự án bằng Vue:

- Trình soạn thảo code được khuyên khích dùng [Visual Studio Code](https://code.visualstudio.com/) + [Volar extension](https://marketplace.visualstudio.com/items?itemName=johnsoncodehk.volar). [WebStorm](https://www.jetbrains.com/webstorm/).
- Chi tiết về các công cụ hỗ trợ, kết hợp phát triển với phía backend (xử lý các thông tin ở phía máy chủ) được thảo luận tại [Tooling Guide](/guide/scaling-up/tooling.html).
- Để tìm hiểu thêm về công cụ xây dựng Vite, hãy xem [Vite docs](https://vitejs.dev).
- Nếu bạn sử dụng TypeScript, hãy xem [TypeScript Usage Guide](typescript/overview.html).

Khi bạn đã sẵn sàng để đưa dự án của mình lên môi trường production, vui lòng nhập dòng lệnh phía dưới:
<div class="language-sh"><pre><code><span class="line"><span style="color:var(--vt-c-green);">&gt; </span><span style="color:#A6ACCD;">npm run build</span></span>
<span class="line"></span></code></pre></div>

Sau khi nhập dòng lệnh trên, các tệp cài đặt cho môi trường production (thương mại) của dự án được chứa ở thư mục `./dist`. Vui lòng xem thêm thông tin về việc đưa sản phẩm lên môi trường production.

[Bước tiếp theo >](#next-steps)

## Không sử dụng công cụ hỗ trợ

To get started with Vue without a build step, simply copy the following code into an HTML file and open it in your browser:

```html
<script src="https://unpkg.com/vue@3"></script>

<div id="app">{{ message }}</div>

<script>
  Vue.createApp({
    data() {
      return {
        message: 'Hello Vue!'
      }
    }
  }).mount('#app')
</script>
```

The above example uses the global build of Vue where all APIs are exposed under the global `Vue` variable.

While the global build works, we will be primarily using [ES modules](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules) syntax throughout the rest of the documentation for consistency. In order to use Vue over native ES modules, use the following HTML instead:

```html
<script type="importmap">
  {
    "imports": {
      "vue": "https://unpkg.com/vue@3/dist/vue.esm-browser.js"
    }
  }
</script>

<div id="app">{{ message }}</div>

<script type="module">
  import { createApp } from 'vue'

  createApp({
    data() {
      return {
        message: 'Hello Vue!'
      }
    }
  }).mount('#app')
</script>
```

Notice how we can import directly from `'vue'` in our code - this is made possible by the `<script type="importmap">` block, leveraging a native browser feature called [Import Maps](https://caniuse.com/import-maps). Import maps are currently only available in Chromium-based browsers, so we recommend using Chrome or Edge during the learning process. If your preferred browser does not support import maps yet, you can polyfill it with [es-module-shims](https://github.com/guybedford/es-module-shims).

You can add entries for other dependencies to the import map - just make sure they point to the ES modules version of the library you intend to use.

:::tip Not for production
The import-maps-based setup is meant for learning only - if you intend to use Vue without build tools in production, make sure to check out the [Production Deployment Guide](/guide/best-practices/production-deployment.html#without-build-tools).
:::

### Serving over HTTP

As we dive deeper into the guide, we may need to split our code into separate JavaScript files so that they are easier to manage. For example:

```html
<!-- index.html -->
<script type="module">
  import { createApp } from 'vue'
  import MyComponent from './my-component.js'

  createApp(MyComponent).mount('#app')
</script>
```

```js
// my-component.js
export default {
  data() {
    return { count: 0 }
  },
  template: `<div>count is {{ count }}</div>`
}
```

In order for this to work, you need to serve your HTML over the `http://` protocol instead of `file://` protocol. To start a local HTTP server, first install [Node.js](https://nodejs.org/en/), and then run `npx serve` from the command line in the same directory where your HTML file is. You can also use any other HTTP server that can serve static files with correct MIME types.

You may have noticed that the imported component's template is inlined as a JavaScript string. If you are using VSCode, you can install the [es6-string-html](https://marketplace.visualstudio.com/items?itemName=Tobermory.es6-string-html) extension and prefix the strings with a `/*html*/` comment to get syntax highlighting for them.

## Next Steps

Chúng tôi thực sự khuyên bạn nên đọc [Hướng dẫn](/guide/introduction) một cách nghiêm túc trước khi bước qua phần tiếp theo.

<div class="vt-box-container next-steps">
  <a class="vt-box" href="/guide/essentials/application.html">
    <p class="next-steps-link">Tiếp tục xem hướng dẫn</p>
    <p class="next-steps-caption">Tài liệu sẽ dẫn bạn qua mọi khía cạnh một cách thật chi tiết.</p>
  </a>
  <a class="vt-box" href="/tutorial/">
    <p class="next-steps-link">Thử làm theo hướng dẫn</p>
    <p class="next-steps-caption">Dành cho những ai thích học bằng cách thực hành.</p>
  </a>
  <a class="vt-box" href="/examples/">
    <p class="next-steps-link">Xem thêm các ví dụ</p>
    <p class="next-steps-caption">Khám phá những ví dụ về các tính năng cơ bản và một vài bài tập về UI (User Interface, giao diện người dùng).</p>
  </a>
</div>
