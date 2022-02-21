---
footer: false
---

# Xuất phát nhanh

Tùy thuộc vào hoàn cảnh sử dụng hay sở thích của bạn, Vue có thể được sử dụng cùng với bước build, hoặc không.

## Với các Công cụ build

Thiết lập công cụ build cho phép chúng ta sử dụng tính năng Vue [Single-File Components](/guide/scaling-up/sfc) (SFCs). Thiết lập công cụ build chính thức của Vue dựa trên [Vite](https://vitejs.dev), một công cụ build frontend hiện đại, nhẹ nhàng và cực kỳ nhanh.

### Trực tuyến (Online)

Bạn có thể thử dùng Vue với tính năng SFCs trực tiếp trên [StackBlitz](https://vite.new/vue). StackBlitz sử dụng Vite để build trực tiếp trên trình duyệt, nên nó gần như giống hệt với thiết lập cục bộ (local) trên máy bạn, nhưng không cần cài đặt thêm bất cứ thứ gì.

### Cục bộ (Local)

:::tip Điều kiện tiên quyết

- Quen thuộc với giao diện dòng lệnh
- Cài đặt [Node.js](https://nodejs.org/)
  :::

Để tạo một dự án Vue với công cụ build trên máy tính của bạn, hãy chạy dòng lệnh sau (không có dấu `>`)

<div class="language-sh"><pre><code><span class="line"><span style="color:var(--vt-c-green);">&gt;</span> <span style="color:#A6ACCD;">npm init vue@latest</span></span></code></pre></div>

Dòng lệnh trên sẽ cài đặt và thực thi công cụ [create-vue](https://github.com/vuejs/create-vue), một công cụ tạo lập dự án mẫu được hỗ trợ chính thức bởi Vue. Giao diện dòng lệnh lúc này sẽ hỏi bạn lựa chọn các tính năng cho dự án như là Typescript hoặc hỗ trợ kiểm thử (testing):

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

Nếu như bạn không chắc chắn về các lựa chọn này, tạm thời cứ tiếp tục chọn `No` bằng cách ấn phím enter. Khi dự án đã được khởi tạo, hãy gõ theo những dòng lệnh hướng dẫn xuất hiện trên màn hình và khởi chạy dev server:

<div class="language-sh"><pre><code><span class="line"><span style="color:var(--vt-c-green);">&gt; </span><span style="color:#A6ACCD;">cd</span><span style="color:#A6ACCD;"> </span><span style="color:#89DDFF;">&lt;</span><span style="color:#888;">your-project-name</span><span style="color:#89DDFF;">&gt;</span></span>
<span class="line"><span style="color:var(--vt-c-green);">&gt; </span><span style="color:#A6ACCD;">npm install</span></span>
<span class="line"><span style="color:var(--vt-c-green);">&gt; </span><span style="color:#A6ACCD;">npm run dev</span></span>
<span class="line"></span></code></pre></div>

Lúc này, bạn đã khởi chạy được dự án Vue đầu tiên! Đây là một số lời khuyên dành cho bạn:

- Thiết lập IDE khuyến nghị là [Visual Studio Code](https://code.visualstudio.com/) + [Volar extension](https://marketplace.visualstudio.com/items?itemName=johnsoncodehk.volar). [WebStorm](https://www.jetbrains.com/webstorm/) cũng là một lựa chọn.
- Chi tiết hơn về các công cụ, bao gồm cả tích hợp với các backend framework, sẽ được thảo luận trong phần [Tooling Guide](/guide/scaling-up/tooling.html).
- Để biết thêm về Vite - công cụ build cơ bản, hãy xem phần [Vite docs](https://vitejs.dev).
- Nếu bạn là một người dùng Typescript, xem thêm phần [TypeScript Usage Guide](typescript/overview.html).

Khi app của bạn đã sẵn sàng cho giai đoạn production, chạy dòng lệnh sau:

<div class="language-sh"><pre><code><span class="line"><span style="color:var(--vt-c-green);">&gt; </span><span style="color:#A6ACCD;">npm run build</span></span>
<span class="line"></span></code></pre></div>

Lệnh này sẽ khởi tạo một bản build production cho app của bạn trong thư mục `./dist` của dự án. Xem phần [Hướng dẫn triển khai Production](/guide/best-practices/production-deployment.html) để tìm hiểu thêm về cách đưa dự án của bạn vào giai đoạn production.

[Bước tiếp theo >](#next-steps)

## Không sử dụng Công cụ build

Để khởi tạo dự án Vue mà không có bước build, hãy sao chép đoạn mã sau vào một tệp HTML và mở nó với trình duyệt của bạn:

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

Ví dụ trên sử dụng bản build global của Vue, khi mà các API đều được hiển thị dưới biến global `Vue`.

Trong khi bản build global hoạt động, chúng ta chủ yếu sử dụng cú pháp [ES mô-đun](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules) trong suốt phần còn lại của tài liệu để mang lại sự nhất quán. Thế nên để sử dụng Vue trên các ES mô-đun gốc, hãy sử dụng đoạn HTML sau thay thế:

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

Giờ hãy chú ý vào cách chúng ta import trực tiếp `'vue'` trong đoạn mã trên - điều này đã được khả thi do chúng ta tận dụng tính năng [Import Maps](https://caniuse.com/import-maps) của trình duyệt, bằng đoạn mã `<script type="importmap">`. Tính năng này hiện tại chỉ khả dụng trên những trình duyệt nhân Chrome, nên chúng tôi khuyến nghị các bạn sử dụng Chrome hoặc phiên bản Edge mới nhất trong quá trình tìm hiểu. Nếu trình duyệt ưa thích của bạn chưa hỗ trợ tính năng import maps, bạn có thể sử dụng polyfill này thay thế [es-module-shims](https://github.com/guybedford/es-module-shims).

Bạn có thể thêm vào import map các thư viện khác - tuy nhiên, hãy đảm bảo rằng chúng phải là phiên bản ES mô-đun của thư viện mà bạn định sử dụng.

:::tip Không dành cho giai đoạn production
Các thiết lập import maps chỉ dành cho quá trình tìm hiểu - nếu bạn có ý định sử Vue mà không có các công cụ build ở giai đoạn production, xin hãy xem kĩ phần [Hướng dẫn triển khai Production](/guide/best-practices/production-deployment.html#without-build-tools).
:::

### Đưa lên HTTP

Để đi sâu hơn vào phần hướng dẫn này, chúng ta có thể phải chia các đoạn mã ra thành từng tệp Javascript riêng biệt để dễ quản lý hơn. Ví dụ:

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

Để chúng hoạt động được, chúng ta cần phải đưa đoạn mã HTML của bạn lên giao thức `http://` thay vì giao thức `file://`. Để khởi chạy một máy chủ HTTP cục bộ, đầu tiên bạn phải cài [Node.js](https://nodejs.org/en/), và chạy dòng lệnh `npx serve` từ cùng một thư mục nơi mà bạn chứa tệp HTML. Bạn cũng có thể sử dụng các máy chủ HTTP khác mà có thể đưa các tệp tĩnh của bạn lên đúng với định dạng MIME của chúng.

Lúc này, có thể bạn sẽ nhận thấy template của component mà bạn đã import vào, được nội tuyến (inline) dưới dạng một chuỗi (string) trong Javascript. Nếu bạn sử dụng VSCode, bạn có thể cài đặt trình mở rộng (extension) [es6-string-html](https://marketplace.visualstudio.com/items?itemName=Tobermory.es6-string-html) và đặt tiền tố `/*html*/` dưới dạng comment vào các chuỗi (string) trên để làm nổi bật cú pháp cho chúng.

## Bước tiếp theo

Nếu bạn đã bỏ qua phần [Giới thiệu](/guide/introduction), chúng tôi cực kỳ khuyến nghị bạn hãy đọc nó trước khi chuyển sang các phần còn lại của tài liệu này.

<div class="vt-box-container next-steps">
  <a class="vt-box" href="/guide/essentials/application.html">
    <p class="next-steps-link">Tiếp tục với Mục chỉ dẫn</p>
    <p class="next-steps-caption">Mục chỉ dẫn này sẽ giúp bạn hiểu được hết từng chi tiết trong các khía cạnh của framework.</p>
  </a>
  <a class="vt-box" href="/tutorial/">
    <p class="next-steps-link">Thử sức với các Bài học</p>
    <p class="next-steps-caption">Cho những người thích học bằng thực tiễn.</p>
  </a>
  <a class="vt-box" href="/examples/">
    <p class="next-steps-link">Xem qua các Ví dụ</p>
    <p class="next-steps-caption">Khám phá các ví dụ của những tính năng cốt lõi và tác vụ UI thông dụng.</p>
  </a>
</div>
