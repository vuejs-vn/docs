---
footer: false
---

# Bắt đầu nhanh

Tùy từng trường hợp hay sở thích, bạn có thể dùng Vue với bước build hoặc không.

## Với các công cụ build

Công cụ build cho phép chúng ta sử dụng [Single-File Component](/guide/scaling-up/sfc) (SFC). Công cụ build chính thức của Vue được dựa trên [Vite](https://vitejs.dev), một công cụ build frontend hiện đại, nhẹ nhàng và cực kỳ nhanh.

### Trực tuyến (Online)

Bạn có thể dùng thử Vue với SFC trực tuyến trên [StackBlitz](https://vite.new/vue). StackBlitz sử dụng Vite để build trực tiếp trên trình duyệt, nên nó gần như giống hệt với thiết lập cục bộ (local) trên máy bạn, nhưng không cần cài đặt thêm bất cứ thứ gì.

### Cục bộ (Local)

:::tip Điều kiện tiên quyết

- Quen thuộc với giao diện dòng lệnh
- Cài đặt [Node.js](https://nodejs.org/)
  :::

Để tạo một dự án Vue với công cụ build trên máy tính của bạn, hãy chạy dòng lệnh sau (không có dấu `>`)

<div class="language-sh"><pre><code><span class="line"><span style="color:var(--vt-c-green);">&gt;</span> <span style="color:#A6ACCD;">npm init vue@latest</span></span></code></pre></div>

Dòng lệnh trên sẽ cài đặt và thực thi [create-vue](https://github.com/vuejs/create-vue), công cụ tạo lập dự án mẫu chính thức của Vue. Giao diện dòng lệnh lúc này sẽ yêu cầu bạn lựa chọn các tính năng cho dự án như TypeScript hoặc hỗ trợ kiểm thử (testing):

<div class="language-sh"><pre><code><span style="color:var(--vt-c-green);">✔</span> <span style="color:#A6ACCD;">Project name: <span style="color:#888;">… <span style="color:#89DDFF;">&lt;</span><span style="color:#888;">your-project-name</span><span style="color:#89DDFF;">&gt;</span></span></span>
<span style="color:var(--vt-c-green);">✔</span> <span style="color:#A6ACCD;">Add TypeScript? <span style="color:#888;">… <span style="color:#89DDFF;text-decoration:underline">No</span> / Yes</span></span>
<span style="color:var(--vt-c-green);">✔</span> <span style="color:#A6ACCD;">Add JSX Support? <span style="color:#888;">… <span style="color:#89DDFF;text-decoration:underline">No</span> / Yes</span></span>
<span style="color:var(--vt-c-green);">✔</span> <span style="color:#A6ACCD;">Add Vue Router for Single Page Application development? <span style="color:#888;">… <span style="color:#89DDFF;text-decoration:underline">No</span> / Yes</span></span>
<span style="color:var(--vt-c-green);">✔</span> <span style="color:#A6ACCD;">Add Pinia for state management? <span style="color:#888;">… <span style="color:#89DDFF;text-decoration:underline">No</span> / Yes</span></span>
<span style="color:var(--vt-c-green);">✔</span> <span style="color:#A6ACCD;">Add Vitest for Unit testing? <span style="color:#888;">… <span style="color:#89DDFF;text-decoration:underline">No</span> / Yes</span></span>
<span style="color:var(--vt-c-green);">✔</span> <span style="color:#A6ACCD;">Add Cypress for both Unit and End-to-End testing? <span style="color:#888;">… <span style="color:#89DDFF;text-decoration:underline">No</span> / Yes</span></span>
<span style="color:var(--vt-c-green);">✔</span> <span style="color:#A6ACCD;">Add ESLint for code quality? <span style="color:#888;">… <span style="color:#89DDFF;text-decoration:underline">No</span> / Yes</span></span>
<span style="color:var(--vt-c-green);">✔</span> <span style="color:#A6ACCD;">Add Prettier for code formating? <span style="color:#888;">… <span style="color:#89DDFF;text-decoration:underline">No</span> / Yes</span></span>
<span></span>
<span style="color:#A6ACCD;">Scaffolding project in ./<span style="color:#89DDFF;">&lt;</span><span style="color:#888;">your-project-name</span><span style="color:#89DDFF;">&gt;</span>...</span>
<span style="color:#A6ACCD;">Done.</span></code></pre></div>

Nếu như bạn không chắc chắn về các lựa chọn này, tạm thời cứ chọn `No` bằng cách ấn phím Enter. Khi dự án đã được khởi tạo, hãy gõ theo những dòng lệnh hướng dẫn xuất hiện trên màn hình và khởi chạy dev server:

<div class="language-sh"><pre><code><span class="line"><span style="color:var(--vt-c-green);">&gt; </span><span style="color:#A6ACCD;">cd</span><span style="color:#A6ACCD;"> </span><span style="color:#89DDFF;">&lt;</span><span style="color:#888;">your-project-name</span><span style="color:#89DDFF;">&gt;</span></span>
<span class="line"><span style="color:var(--vt-c-green);">&gt; </span><span style="color:#A6ACCD;">npm install</span></span>
<span class="line"><span style="color:var(--vt-c-green);">&gt; </span><span style="color:#A6ACCD;">npm run dev</span></span>
<span class="line"></span></code></pre></div>

Vạy là bạn đã khởi chạy được dự án Vue đầu tiên! Sau đây là một số lời khuyên:

- Thiết lập IDE khuyến nghị là [Visual Studio Code](https://code.visualstudio.com/) + [Volar extension](https://marketplace.visualstudio.com/items?itemName=johnsoncodehk.volar). Bạn cũng có thể dùng [WebStorm](https://www.jetbrains.com/webstorm/).
- Chi tiết hơn về các công cụ, bao gồm cả tích hợp với các backend framework, sẽ được thảo luận trong phần [Hướng dẫn về công cụ](/guide/scaling-up/tooling.html).
- Để biết thêm về Vite, hãy đọc [tài liệu của Vite](https://vitejs.dev).
- Nếu bạn dùng TypeScript, xem thêm phần [Hướng dẫn sử dụng TypeScript](typescript/overview.html).

Khi đã sẵn sàng đưa app lên môi trường production, chạy dòng lệnh sau:

<div class="language-sh"><pre><code><span class="line"><span style="color:var(--vt-c-green);">&gt; </span><span style="color:#A6ACCD;">npm run build</span></span>
<span class="line"></span></code></pre></div>

Lệnh này sẽ khởi tạo một bản build production cho app của bạn trong thư mục `./dist` của dự án. Xem phần [Hướng dẫn triển khai Production](/guide/best-practices/production-deployment.html) để tìm hiểu thêm về cách đưa dự án của bạn lên production.

[Bước tiếp theo >](#next-steps)

## Không sử dụng công cụ build

Để khởi tạo dự án Vue mà không có bước build, hãy sao chép đoạn mã sau vào một file HTML và mở file này trong trình duyệt:

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

Ví dụ trên sử dụng bản build global của Vue, với toàn bộ API có sẵn (exposed) trong biến toàn cục `Vue`.

Tuy hoàn toàn có thể dùng bản build global của Vue, trong suốt phần còn lại của tài liệu này chúng ta chủ yếu sẽ sử dụng cú pháp [ES module](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules) cho nhất quán. Để sử dụng Vue với ES module, hãy dùng đoạn HTML sau:

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

Lưu ý vào cách chúng ta import trực tiếp `'vue'` trong đoạn mã trên - sở dĩ điều này khả thi là do chúng ta đã tận dụng tính năng [Import Maps](https://caniuse.com/import-maps) của trình duyệt bằng đoạn mã `<script type="importmap">`. Hiện tại tính năng này chỉ mới được hỗ trợ trên những  trình duyệt nhân Chromium, vì thế các bạn nên dùng Chrome hoặc Edge trong quá trình tìm hiểu. Nếu trình duyệt của bạn chưa hỗ trợ import maps, bạn có thể sử dụng polyfill [es-module-shims](https://github.com/guybedford/es-module-shims) thay thế.

Bạn có thể thêm các thư viện khác vào import map  - chỉ cần đảm bảo rằng chúng phải là phiên bản ES module của thư viện mà bạn định sử dụng.

:::tip Không dành cho môi trường production
Thiết lập dựa trên import maps chỉ dành cho quá trình tìm hiểu - nếu bạn có ý định sử Vue mà không có các công cụ build trong môi trường production, hãy xem phần [Hướng dẫn triển khai production](/guide/best-practices/production-deployment.html#without-build-tools).
:::

### Serve bằng HTTP

Đi sâu hơn vào phần hướng dẫn, chúng ta có thể phải chia code ra thành các file JavaScript riêng biệt để dễ quản lý hơn. Ví dụ:

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

Để phương thức này hoạt động, bạn cần phải serve (cung cấp) HTML qua giao thức `http://` thay vì giao thức `file://`. Để khởi chạy một server HTTP cục bộ, đầu tiên bạn phải cài [Node.js](https://nodejs.org/en/), và chạy dòng lệnh `npx serve` từ thư mục chứa file HTML. Bạn cũng có thể sử dụng các server HTTP khác, miễn là các file tĩnh được serve với đúng [MIME type](https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/MIME_types).

Có lẽ bạn đã nhận thấy template của component mà bạn đã import vào nằm ở dạng chuỗi (string) JavaScript. Nếu sử dụng VSCode, bạn có thể cài đặt trình mở rộng (extension) [es6-string-html](https://marketplace.visualstudio.com/items?itemName=Tobermory.es6-string-html) và thêm `/*html*/` vào trước các chuỗi trên để làm nổi bật cú pháp cho các chuỗi này.

## Các bước tiếp theo

Bạn rất nên đọc phần [Giới thiệu](/guide/introduction) (nếu chưa đọc) trước khi tiếp tục với các phần còn lại của tài liệu này.

<div class="vt-box-container next-steps">
  <a class="vt-box" href="/guide/essentials/application.html">
    <p class="next-steps-link">Tiếp tục với Hướng dẫn</p>
    <p class="next-steps-caption">Giúp bạn hiểu chi tiết đến từng ngóc ngách của framework.</p>
  </a>
  <a class="vt-box" href="/tutorial/">
    <p class="next-steps-link">Thử sức với các bài thực hành</p>
    <p class="next-steps-caption">Cho những người thích học bằng phương pháp thực tiễn.</p>
  </a>
  <a class="vt-box" href="/examples/">
    <p class="next-steps-link">Xem ví dụ</p>
    <p class="next-steps-caption">Khám phá các ví dụ về những tính năng chủ chốt và tác vụ UI thông dụng.</p>
  </a>
</div>
