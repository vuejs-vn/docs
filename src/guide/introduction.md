---
footer: false
---

# Giới Thiệu

:::info Bạn đang đọc tài liệu cho Vue 3!

- Tài liệu của Vue 2 đã được chuyển về trang [v2.vuejs.org](https://v2.vuejs.org/).
- Xem hướng dẫn nâng cấp từ Vue 2: [Hướng dẫn nâng cấp](https://v3-migration.vuejs.org/).
  :::

## Vue là gì?

Vue (phát âm: /vjuː/, giống **view**) là một JavaScript framework dùng để xây dựng giao diện người dùng. Nó được xây dựng trên nền tảng HTML, CSS và JavaScript, cung cấp mô hình lập trình declarative và component-based, giúp bạn phát triển giao diện người dùng một cách hiệu quả hơn, dù nó đơn giản hay phức tạp.

Đây là một ví dụ nhỏ:

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

- **Declarative Rendering**: Vue sử dụng HTML để làm template, đồng thời mở rộng nó để cho phép chúng ta mô tả HTML (sau khi render) dựa trên trạng thái của (biến, variable) JavaScript.

- **Reactivity**: Vue tự động theo dõi sự thay đổi của các giá trị trong JavaScript và cập nhật DOM một cách hiệu.

Có thể bạn đang có nhiều thắc mắc - đừng lo. Chúng tôi sẽ giải thích một cách rất chi tiết trong phần còn lại của tài liệu. Còn bây giờ, hãy cứ tiếp tục đọc để có một cái nhìn tổng quan về những gì Vue cung cấp.

:::tip Yêu cầu
Phần còn lại của tài liệu đòi hỏi một số kinh nghiệm với HTML, CSS và JavaScript. Nếu bạn hoàn toàn chưa có kinh nghiệm gì với frontend, thì việc tìm hiểu ngay một framework không phải là lựa chọn tốt nhất lúc này - hãy tìm hiểu các kiến thức cơ bản trước rồi quay lại! Kinh nghiệm với các framework khác có thể sẽ hữu ích, nhưng không bắt buộc.
:::

## Một Framework Cấp Tiến

Vue là một framework và hệ sinh thái của nó bao gồm hầu như đầy đủ các các tính năng cần thiết trong quá trình phát triển frontend. Nhưng môi trường web thì cực kì đa dạng - những thứ chúng ta xây dựng trên web có thể khác nhau một cách đáng kể về hình thức và quy mô. Với suy nghĩ đó, Vue được thiết kế để trở nên linh hoạt và có thể áp dụng từng phần (dần dần). Tùy thuộc vào từng trường hợp, Vue có thể được sử dụng theo những cách khác nhau:

- Cải thiện HTML tĩnh mà không cần build
- Nhúng vào page như là một Web Component
- Single-Page Application (SPA)
- Fullstack / Server-Side-Rendering (SSR)
- JAMStack / Static-Site-Generation (SSG)
- Xây dựng ứng dụng desktop, mobile, WebGL hoặc thậm chí là terminal

Nếu bạn thấy những khái niệm này đáng sợ, đừng lo lắng! Phần hướng dẫn và chỉ dẫn này chỉ yêu cầu kiến thức cơ bản về HTML và JavaScript và bạn sẽ có thể làm theo mà không cần phải là chuyên gia về bất kỳ thứ nào trong số này.

Nếu bạn là một developer có kinh nghiệm, quan tâm đến cách tích hợp tốt nhất Vue vào stack của mình hoặc bạn tò mò về ý nghĩa của các thuật ngữ này, chúng tôi sẽ thảo luận chi tiết hơn về chúng trong [Cách sử dụng Vue](/guide/extras/ways-of-using-vue).

Bất chấp tính linh hoạt, kiến thức cốt lõi về cách Vue hoạt động áp dụng được cho tất cả các trường hợp trên. Ngay cả khi bạn chỉ là người mới bắt đầu, kiến thức thu được trong quá học này sẽ vẫn hữu ích khi bạn thực hiện các mục tiêu tham vọng hơn trong tương lai. Nếu bạn đã có nhiều kinh nghiệm, bạn có thể chọn cách tối ưu để tận dụng Vue dựa trên các vấn đề bạn đang cố gắng giải quyết, trong khi vẫn giữ nguyên năng suất. Đây là lý do tại sao chúng tôi gọi Vue là "framework Cấp Tiến": đó là một framework có thể phát triển cùng với bạn và thích ứng với nhu cầu của bạn.

## Single-File Components

Trong hầu hếu những dự án Vue có dùng build-tool, chúng tôi tạo ra những component sử dụng định dạng giống với HTML gọi là **Single-File Component** (còn được biết đến là các file `*.vue`, viết tắt là **SFC**). Một SFC, như tên của nó, đóng gói các thành phần của một component như logic (JavaScript), template (HTML), và style (CSS) trong một file duy nhất. Hãy viết lại ví dụ phía trên theo kiểu SFC:

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

SFC is a defining feature of Vue, and is the recommended way to author Vue components **if** your use case warrants a build setup. You can learn more about the [how and why of SFC](/guide/scaling-up/sfc) in its dedicated section - but for now, just know that Vue will handle all the build tools setup for you.

## Các kiêu API

Vue component có thể được viết bằng hai kiểu API khác nhau: **Options API** và **Composition API**.

### Options API

Với Option API, chúng ta định nghĩa logic của component bằng cách sử dụng các thuộc tính của option object, ví dụ như `data`, `methods`, và `mounted`. Các function nằm trong options có thể truy cập tới các thuộc tính khác của options thông qua `this`, `this` trỏ tới instance của component.

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
  // They can be bound as event listeners in templates.
  // Chúng có thể đóng vai trò như event listener trong template.
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

### Composition API thường được sử dụng với [`<script setup>`](/api/sfc-script-setup).

With Composition API, we define a component's logic using imported API functions. In SFCs, Composition API is typically used with [`<script setup>`](/api/sfc-script-setup). The `setup` attribute is a hint that makes Vue perform compile-time transforms that allow us to use Composition API with less boilerplate. For example, imports and top-level variables / functions declared in `<script setup>` are directly usable in the template.

Với Composition API, chúng ta định nghĩa logic của component bằng cách sử dụng các API được import. Trong SFCs, Composition API thường được sử dụng với [`<script setup>`](/api/sfc-script-setup). Thuộc tính `setup` nhưng m

Here is the same component, with the exact same template, but using Composition API and `<script setup>` instead:

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

[Try it in the Playground](https://sfc.vuejs.org/#eyJBcHAudnVlIjoiPHNjcmlwdCBzZXR1cD5cbmltcG9ydCB7IHJlZiwgb25Nb3VudGVkIH0gZnJvbSAndnVlJ1xuXG4vLyByZWFjdGl2ZSBzdGF0ZVxuY29uc3QgY291bnQgPSByZWYoMClcblxuLy8gZnVuY3Rpb25zIHRoYXQgbXV0YXRlIHN0YXRlIGFuZCB0cmlnZ2VyIHVwZGF0ZXNcbmZ1bmN0aW9uIGluY3JlbWVudCgpIHtcbiAgY291bnQudmFsdWUrK1xufVxuXG4vLyBsaWZlY3ljbGUgaG9va3Ncbm9uTW91bnRlZCgoKSA9PiB7XG4gIGNvbnNvbGUubG9nKGBUaGUgaW5pdGlhbCBjb3VudCBpcyAke2NvdW50LnZhbHVlfS5gKVxufSlcbjwvc2NyaXB0PlxuXG48dGVtcGxhdGU+XG4gIDxidXR0b24gQGNsaWNrPVwiaW5jcmVtZW50XCI+Y291bnQgaXM6IHt7IGNvdW50IH19PC9idXR0b24+XG48L3RlbXBsYXRlPiJ9)

### Which to Choose?

First of all, both API styles are fully capable of covering common use cases. They are different interfaces powered by the exact same underlying system. In fact, the Options API is implemented on top of the Composition API! The fundamental concepts and knowledge about Vue are shared across the two styles.

The Options API is centered around the concept of a "component instance" (`this` as seen in the example), which typically aligns better with a class-based mental model for users coming from OOP language backgrounds. It is also more beginner-friendly by abstracting away the reactivity details and enforcing code organization via option groups.

The Composition API is centered around declaring reactive state variables directly in a function scope, and composing state from multiple functions together to handle complexity. It is more free-form, and requires understanding of how reactivity works in Vue to be used effectively. In return, its flexibility enables more powerful patterns for organizing and reusing logic.

You can learn more about the comparison between the two styles and the potential benefits of Composition API in the [Composition API FAQ](/guide/extras/composition-api-faq).

If you are new to Vue, here's our general recommendation:

- For learning purposes, go with the style that looks easier to understand to you. Again, most of the core concepts are shared between the two styles. You can always pick up the other one at a later time.

- For production use:

  - Go with Options API if you are not using build tools, or plan to use Vue primarily in low-complexity scenarios, e.g. progressive enhancement.

  - Go with Composition API + Single-File Components if you plan to build full applications with Vue.

You don't have to commit to only one style during the learning phase. The rest of the documentation will provide code samples in both styles where applicable, and you can toggle between them at any time using the **API Preference switches** at the top of the left sidebar.

## Bạn vẫn còn thắc mắc?

Hãy xem qua trang [Hỏi Đáp](/about/faq).

## Pick Your Learning Path

Different developers have different learning styles. Feel free to pick a learning path that suits your preference - although we do recommend going over all content if possible!

<div class="vt-box-container next-steps">
  <a class="vt-box" href="/tutorial/">
    <p class="next-steps-link">Try the Tutorial</p>
    <p class="next-steps-caption">For those who prefer learning things hands-on.</p>
  </a>
  <a class="vt-box" href="/guide/quick-start.html">
    <p class="next-steps-link">Read the Guide</p>
    <p class="next-steps-caption">The guide walks you through every aspect of the framework in full details.</p>
  </a>
  <a class="vt-box" href="/examples/">
    <p class="next-steps-link">Check out the Examples</p>
    <p class="next-steps-caption">Explore examples of core features and common UI tasks.</p>
  </a>
</div>
