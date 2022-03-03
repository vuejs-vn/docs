---
footer: false
---

# Giới thiệu

:::info Bạn đang đọc tài liệu của Vue 3!

- Tài liệu của Vue 2 đã được chuyển về trang [v2.vuejs.org](https://v2.vuejs.org/).
- Xem hướng dẫn nâng cấp từ Vue 2: [Hướng dẫn nâng cấp](https://v3-migration.vuejs.org/).
  :::

## Vue là gì?

Vue (phát âm: /vjuː/, giống **view**) là một framework JavaScript dùng để xây dựng giao diện người dùng. Vue xây dựng trên nền tảng HTML, CSS và JavaScript, cung cấp mô hình lập trình khai báo (declarative) và dựa trên component (component-based), giúp bạn phát triển giao diện người dùng — bất kể là đơn giản hay phức tạp — một cách hiệu quả.

Đây là một ví dụ đơn giản:

```js
import { createApp } from 'vue'

createApp({
  data() {
    return {
      count: 0
    }
  }
}).mount('#app')
```

```vue-html
<div id="app">
  <button @click="count++">
    Count is: {{ count }}
  </button>
</div>
```

**Kết quả**

<script setup>
import { ref } from 'vue'
const count = ref(0)
</script>

<div class="demo">
  <button @click="count++">
    Count is: {{ count }}
  </button>
</div>

Ví dụ phía trên thể hiện hai tính năng của Vue:

- **Declarative Rendering**: Vue sử dụng HTML để làm template, đồng thời mở rộng nó để cho phép chúng ta mô tả output HTML (sau khi render) dựa trên trạng thái của JavaScript.

- **Reactivity**: Vue tự động theo dõi sự thay đổi của các giá trị trong JavaScript và cập nhật DOM một cách hiệu quả.

Có thể bạn đang có nhiều thắc mắc - đừng lo. Chúng tôi sẽ giải thích một cách rất chi tiết trong phần còn lại của tài liệu. Còn bây giờ, hãy cứ tiếp tục đọc để có một cái nhìn tổng quan về những gì Vue cung cấp.

:::tip Yêu cầu
Phần còn lại của tài liệu đòi hỏi một số kinh nghiệm với HTML, CSS và JavaScript. Nếu bạn hoàn toàn chưa có kinh nghiệm gì với frontend, thì việc tìm hiểu ngay một framework không phải là lựa chọn tốt nhất lúc này - hãy tìm hiểu các kiến thức cơ bản trước rồi quay lại sau! Kinh nghiệm với các framework khác có thể sẽ hữu ích, nhưng không bắt buộc.
:::

## Một framework linh động

Vue là một framework và hệ sinh thái của nó bao gồm hầu như đầy đủ các các tính năng cần thiết trong quá trình phát triển frontend. Nhưng môi trường web thì cực kì đa dạng - những thứ chúng ta xây dựng trên web có thể khác nhau một cách đáng kể về hình thức và quy mô. Với suy nghĩ đó, Vue được thiết kế để trở nên linh hoạt và có thể áp dụng từng phần (dần dần). Tùy thuộc vào từng trường hợp, Vue có thể được sử dụng theo những cách khác nhau:

- Cải thiện HTML tĩnh mà không cần build
- Nhúng vào page như là một Web Component
- Single-Page Application (SPA)
- Fullstack / Server-Side-Rendering (SSR)
- JAMStack / Static-Site-Generation (SSG)
- Xây dựng ứng dụng desktop, mobile, WebGL hoặc thậm chí là terminal

Nếu bạn thấy những khái niệm này đáng sợ, đừng lo lắng! Phần hướng dẫn và chỉ dẫn này chỉ yêu cầu kiến thức cơ bản về HTML và JavaScript và bạn sẽ có thể làm theo mà không cần phải là chuyên gia về bất kỳ thứ nào trong số chúng.

Nếu bạn là một developer có kinh nghiệm, quan tâm đến cách tốt nhất để tích hợp Vue vào stack của mình hoặc bạn tò mò về các cách sử dụng trên, chúng tôi sẽ thảo luận chi tiết hơn về chúng trong [Cách sử dụng Vue](/guide/extras/ways-of-using-vue).

Bất chấp tính linh hoạt, kiến thức cốt lõi về cách Vue hoạt động áp dụng được cho tất cả các trường hợp trên. Ngay cả khi bạn chỉ là người mới bắt đầu, kiến thức thu được trong quá học này sẽ vẫn hữu ích khi bạn thực hiện các mục tiêu tham vọng hơn trong tương lai. Nếu bạn đã có nhiều kinh nghiệm, bạn có thể chọn cách tối ưu để tận dụng Vue dựa trên các vấn đề bạn đang cố gắng giải quyết, trong khi vẫn giữ nguyên năng suất. Đây là lý do tại sao chúng tôi gọi Vue là "framework linh động": đó là một framework có thể phát triển cùng với bạn và thích ứng với nhu cầu của bạn.

## Single-File Components

Trong hầu hếu những dự án Vue có dùng công cụ build, chúng tôi tạo ra những component sử dụng định dạng giống với HTML gọi là **Single-File Component** (còn được biết đến là các file `*.vue`, viết tắt là **SFC**). Một SFC, như tên của nó, đóng gói các thành phần của một component như logic (JavaScript), template (HTML), và style (CSS) trong một file duy nhất. Đây là ví dụ phía trên, nhưng được viết bằng SFC:

```vue
<script>
export default {
  data() {
    return {
      count: 0
    }
  }
}
</script>

<template>
  <button @click="count++">Count is: {{ count }}</button>
</template>

<style scoped>
button {
  font-weight: bold;
}
</style>
```

SFC là một tính năng đặt trưng của Vue, và nó được khuyến khích để tạo các component trong Vue **nếu** trường hợp sử dụng của bạn có cài đặt công cụ build. Bạn có thể tìm hiểu thêm về [cách và lý do dùng SFC](/guide/scaling-up/sfc) trong phần riêng của nó - nhưng hiện tại, chỉ cần biết rằng Vue sẽ xử lý việc cài đặt công cụ build cho bạn.

## Các kiểu API

Vue component có thể được viết bằng hai kiểu API khác nhau: **Options API** và **Composition API**.

### Options API

Với Option API, chúng ta định nghĩa logic của component bằng cách sử dụng các thuộc tính của một option object, ví dụ như `data`, `methods`, và `mounted`. Các function nằm trong option có thể truy cập tới các thuộc tính khác của option đó thông qua `this`, `this` trỏ tới instance của component.

```vue
<script>
export default {
  // Các thuộc tính được trả về bởi data() sẽ trở thành reactive state và được truy cập thông qua `this`.
  data() {
    return {
      count: 0
    }
  },
  
  // methods là những function sẽ thay đổi state và kích hoạt các cập nhật (template, watch, computed, ...).
  // Có thể dùng chúng để lắng nghe event trong template.
  methods: {
    increment() {
      this.count++
    }
  },
  
  // Lifecycle hooks được được gọi ở các giai đoạn khác trong trong vòng đời của component.
  // Function dưới này sẽ được gọi khi component được mount.
  mounted() {
    console.log(`The initial count is ${this.count}.`)
  }
}
</script>

<template>
  <button @click="increment">count is: {{ count }}</button>
</template>
```

[Thử nó trong Playground](https://sfc.vuejs.org/#eyJBcHAudnVlIjoiPHNjcmlwdD5cbmV4cG9ydCBkZWZhdWx0IHtcbiAgLy8gcmVhY3RpdmUgc3RhdGVcbiAgZGF0YSgpIHtcbiAgICByZXR1cm4ge1xuICAgICAgY291bnQ6IDBcbiAgICB9XG4gIH0sXG5cbiAgLy8gZnVuY3Rpb25zIHRoYXQgbXV0YXRlIHN0YXRlIGFuZCB0cmlnZ2VyIHVwZGF0ZXNcbiAgbWV0aG9kczoge1xuICAgIGluY3JlbWVudCgpIHtcbiAgICAgIHRoaXMuY291bnQrK1xuICAgIH1cbiAgfSxcblxuICAvLyBsaWZlY3ljbGUgaG9va3NcbiAgbW91bnRlZCgpIHtcbiAgICBjb25zb2xlLmxvZyhgVGhlIGluaXRpYWwgY291bnQgaXMgJHt0aGlzLmNvdW50fS5gKVxuICB9XG59XG48L3NjcmlwdD5cblxuPHRlbXBsYXRlPlxuICA8YnV0dG9uIEBjbGljaz1cImluY3JlbWVudFwiPmNvdW50IGlzOiB7eyBjb3VudCB9fTwvYnV0dG9uPlxuPC90ZW1wbGF0ZT4ifQ==)

### Composition API

Với Composition API, chúng ta định nghĩa logic của component bằng cách sử dụng các API được import. Trong SFCs, Composition API thường được sử dụng với [`<script setup>`](/api/sfc-script-setup). Thuộc tính `setup` là một gợi ý giúp Vue thực hiện thêm một số chuyển đổi khi biên dịch, cho phép chúng ta sử dụng Composition API với ít code hơn. Ví dụ, các function và variable được import hoặc khai báo trong ngữ cảnh hiện tại có thể được dùng trực tiếp trong template.

Đây là component tương tự như trên, với cùng tempalte, nhưng sử dụng Composition API và `<script setup>`:

```vue
<script setup>
import { ref, onMounted } from 'vue'

// reactive state
const count = ref(0)

// functions that mutate state and trigger updates
function increment() {
  count.value++
}

// lifecycle hooks
onMounted(() => {
  console.log(`The initial count is ${count.value}.`)
})
</script>

<template>
  <button @click="increment">Count is: {{ count }}</button>
</template>
```

[Thử nó trong Playground](https://sfc.vuejs.org/#eyJBcHAudnVlIjoiPHNjcmlwdCBzZXR1cD5cbmltcG9ydCB7IHJlZiwgb25Nb3VudGVkIH0gZnJvbSAndnVlJ1xuXG4vLyByZWFjdGl2ZSBzdGF0ZVxuY29uc3QgY291bnQgPSByZWYoMClcblxuLy8gZnVuY3Rpb25zIHRoYXQgbXV0YXRlIHN0YXRlIGFuZCB0cmlnZ2VyIHVwZGF0ZXNcbmZ1bmN0aW9uIGluY3JlbWVudCgpIHtcbiAgY291bnQudmFsdWUrK1xufVxuXG4vLyBsaWZlY3ljbGUgaG9va3Ncbm9uTW91bnRlZCgoKSA9PiB7XG4gIGNvbnNvbGUubG9nKGBUaGUgaW5pdGlhbCBjb3VudCBpcyAke2NvdW50LnZhbHVlfS5gKVxufSlcbjwvc2NyaXB0PlxuXG48dGVtcGxhdGU+XG4gIDxidXR0b24gQGNsaWNrPVwiaW5jcmVtZW50XCI+Y291bnQgaXM6IHt7IGNvdW50IH19PC9idXR0b24+XG48L3RlbXBsYXRlPiJ9)

### Nên chọn kiểu API nào?

Đầu tiên, cả hai kiểu API đều có thể được sử dụng trong các trường hợp thường gặp Chúng là hai phương thức khác nhau được cung cấp bởi cùng một hệ thống. Thực ra, Options API được xây dựng dựa trên Composition API! Các khái niệm nền tảng và kiến thức về Vue đều được dùng chung trong cả hai kiểu.

Options API tập trung vào khái niệm của "component instance" (như `this` trong ví dụ trên), nó phù hợp với mô hình lập trình dựa trên class của những người dùng đến từ các ngôn ngữ lập trình hướng đối tượng. Nó cũng thân thiện hơn với người mới bằng cách trừu tượng hóa các chi tiết và thực thi sự tổ chức code thông qua các nhóm option.

Composition API tập trung vào việc khai báo các biến reactive trực tiếp trong phạm vi của một function, và sử dụng nó trong nhiều function khác nhau để giải quyết các vấn đề phức tạp. Nó ít khuôn mẫu, và đòi hỏi hiểu biết về cách mà reactive hoạt động trong Vue để có thể được sử dụng một cách hiệu quả. Đổi lại, tính linh hoạt của nó cho phép sử dụng nhiều pattern mạnh mẽ để tổ chức và sử dụng lại logic.

Bạn có thể tìm hiểu thêm về sự so sánh giữa hai kiểu API này và những lợi ích tiềm năng của Composition API tại trang [Hỏi đáp về Composition API](/guide/extras/composition-api-faq).

Nếu bạn mới tìm hiểu Vue, đây là gợi ý chung của chúng tôi:

- Đối với mục đích học tập, hãy chọn kiểu mà bạn cảm thấy đễ hiểu nhất. Một lần nữa, hầu như mọi khái niệm cốt lõi đều được chia sẻ giữa hai kiểu. Sau này bạn luôn có thể chọn kiểu còn lại.

- Để xây dựng sản phẩm:

  - Chọn Options API nếu bạn không dùng công cụ build, hoặc định sử dụng Vue vào những tình huống ít phức tạp, ví dụ như nâng cấp từng bước (progressive enhancement).
  
  - Chọn Composition API + Single-File Components nếu bạn định xây dựng những ứng dụng hoàn toàn bằng Vue.

Bạn không nhất thiết phải sử dụng cố định một kiểu duy nhất trong giai đoạn học này. Phần còn lại của tài liệu sẽ chung cấp code mẫu ở cả hai kiểu nếu có thể, và bạn có thể thay đổi giữa hai kiểu này bằng cách sử dụng **nút chuyển đổi kiểu API** ở phía trên của sidebar trái.

## Bạn vẫn còn thắc mắc?

Hãy xem qua trang [Hỏi Đáp](/about/faq).

## Chọn con đường học tập của bạn

Những lập trình viên khác nhau có những phong cách học tập khác nhau. Hãy tự nhiên chọn con đường học tập phù hợp với sơ thích cá nhân - mặc dù chúng tôi khuyến nghị nên đọc hết hếu có thể!

<div class="vt-box-container next-steps">
  <a class="vt-box" href="/tutorial/">
    <p class="next-steps-link">Hướng dẫn từng bước</p>
    <p class="next-steps-caption">Dành cho ai thích học thông qua thực hành.</p>
  </a>
  <a class="vt-box" href="/guide/quick-start.html">
    <p class="next-steps-link">Đọc tài liệu</p>
    <p class="next-steps-caption">Tài liệu sẽ hướng dẫn bạn một cách chi tiết về mọi khía cạnh của framework.</p>
  </a>
  <a class="vt-box" href="/examples/">
    <p class="next-steps-link">Xem ví dụ</p>
    <p class="next-steps-caption">Khám phá các ví dụ về những tính năng cốt lõi và tác vụ giao diện người dùng phổ biến.</p>
  </a>
</div>
