# Thuộc tính computed

## Ví dụ cơ bản

Các biểu thức (expression) trong template rất tiện lợi, nhưng chỉ nên dùng cho các tác vụ đơn giản. Đặt quá nhiều logic có thể template phình to ra và khó bảo trì. Ví dụ, nếu chúng ta có object trong chứa một mảng:

<div class="options-api">

```js
export default {
  data() {
    return {
      author: {
        name: 'John Doe',
        books: [
          'Vue 2 - Advanced Guide',
          'Vue 3 - Basic Guide',
          'Vue 4 - The Mystery'
        ]
      }
    }
  }
}
```

</div>
<div class="composition-api">

```js
const author = reactive({
  name: 'John Doe',
  books: [
    'Vue 2 - Advanced Guide',
    'Vue 3 - Basic Guide',
    'Vue 4 - The Mystery'
  ]
})
```

</div>

Và chúng ta muốn hiển thị những thông điệp khác nhau dựa trên điều kiện `author` đã có sách hay chưa:

```vue-html
<p>Has published books:</p>
<span>{{ author.books.length > 0 ? 'Yes' : 'No' }}</span>
```

Tại điểm này, template �bắt đầu trở nên lộn xộn. �Ta phải mất một chút mới nhận ra là template thực hiện một tính toán dựa trên `author.books`. Quan trọng hơn, chúng ta không muốn lặp lại code nếu cần thêm tính toán này vào template nhiều lần.

Đó là lý do vì sao đối với những logic phức tạp có kèm dữ liệu reactive, bạn nên sử dụng một **thuộc tính computed**. Đây là ví dụ trên được viết lại:

<div class="options-api">

```js
export default {
  data() {
    return {
      author: {
        name: 'John Doe',
        books: [
          'Vue 2 - Advanced Guide',
          'Vue 3 - Basic Guide',
          'Vue 4 - The Mystery'
        ]
      }
    }
  },
  computed: {
    // a computed getter
    publishedBooksMessage() {
      // `this` points to the component instance
      return this.author.books.length > 0 ? 'Yes' : 'No'
    }
  }
}
```

```vue-html
<p>Has published books:</p>
<span>{{ publishedBooksMessage }}</span>
```

[Thử trong Playground](https://sfc.vuejs.org/#eyJBcHAudnVlIjoiPHNjcmlwdD5cbmV4cG9ydCBkZWZhdWx0IHtcbiAgZGF0YSgpIHtcbiAgICByZXR1cm4ge1xuICAgICAgYXV0aG9yOiB7XG4gICAgICAgIG5hbWU6ICdKb2huIERvZScsXG4gICAgICAgIGJvb2tzOiBbXG4gICAgICAgICAgJ1Z1ZSAyIC0gQWR2YW5jZWQgR3VpZGUnLFxuICAgICAgICAgICdWdWUgMyAtIEJhc2ljIEd1aWRlJyxcbiAgICAgICAgICAnVnVlIDQgLSBUaGUgTXlzdGVyeSdcbiAgICAgICAgXVxuICAgICAgfVxuICAgIH1cbiAgfSxcbiAgY29tcHV0ZWQ6IHtcbiAgICBwdWJsaXNoZWRCb29rc01lc3NhZ2UoKSB7XG4gICAgICByZXR1cm4gdGhpcy5hdXRob3IuYm9va3MubGVuZ3RoID4gMCA/ICdZZXMnIDogJ05vJ1xuICAgIH1cbiAgfVxufVxuPC9zY3JpcHQ+XG5cbjx0ZW1wbGF0ZT5cbiAgPHA+SGFzIHB1Ymxpc2hlZCBib29rczo8L3A+XG4gIDxzcGFuPnt7IGF1dGhvci5ib29rcy5sZW5ndGggPiAwID8gJ1llcycgOiAnTm8nIH19PC9zcGFuPlxuPC90ZW1wbGF0ZT4iLCJpbXBvcnQtbWFwLmpzb24iOiJ7XG4gIFwiaW1wb3J0c1wiOiB7XG4gICAgXCJ2dWVcIjogXCJodHRwczovL3NmYy52dWVqcy5vcmcvdnVlLnJ1bnRpbWUuZXNtLWJyb3dzZXIuanNcIlxuICB9XG59In0=)

Ở đây chúng ta đã khai báo một thuộc tính computed `publishedBooksMessage`.

Thử thay đổi giá trị của mảng `books` trong `data` của app và bạn sẽ thấy `publishedBooksMessage` thay đổi tương ứng.

Bạn có thể ràng buộc (data-bind) các thuộc tính computed vào template giống bình thường. Vue biết rằng `this.publishedBooksMessage` phụ thuộc vào `this.author.books` và sẽ cập nhật mọi ràng buộc phụ thuộc vào `this.publishedBooksMessage` khi `this.author.books` thay đổi.

Xem thêm: [Đặt kiểu cho computed property](/guide/typescript/options-api.html#typing-computed-properties) <sup class="vt-badge ts" />

</div>

<div class="composition-api">

```vue
<script setup>
import { reactive, computed } from 'vue'

const author = reactive({
  name: 'John Doe',
  books: [
    'Vue 2 - Advanced Guide',
    'Vue 3 - Basic Guide',
    'Vue 4 - The Mystery'
  ]
})

// a computed ref
const publishedBooksMessage = computed(() => {
  return author.books.length > 0 ? 'Yes' : 'No'
})
</script>

<template>
  <p>Has published books:</p>
  <span>{{ publishedBooksMessage }}</span>
</template>
```

[Thử trong Playground](https://sfc.vuejs.org/#eyJBcHAudnVlIjoiPHNjcmlwdCBzZXR1cD5cbmltcG9ydCB7IHJlYWN0aXZlLCBjb21wdXRlZCB9IGZyb20gJ3Z1ZSdcblxuY29uc3QgYXV0aG9yID0gcmVhY3RpdmUoe1xuICBuYW1lOiAnSm9obiBEb2UnLFxuICBib29rczogW1xuICAgICdWdWUgMiAtIEFkdmFuY2VkIEd1aWRlJyxcbiAgICAnVnVlIDMgLSBCYXNpYyBHdWlkZScsXG4gICAgJ1Z1ZSA0IC0gVGhlIE15c3RlcnknXG4gIF1cbn0pXG5cbi8vIGEgY29tcHV0ZWQgcmVmXG5jb25zdCBwdWJsaXNoZWRCb29rc01lc3NhZ2UgPSBjb21wdXRlZCgoKSA9PiB7XG4gIHJldHVybiBhdXRob3IuYm9va3MubGVuZ3RoID4gMCA/ICdZZXMnIDogJ05vJ1xufSlcbjwvc2NyaXB0PlxuXG48dGVtcGxhdGU+XG4gIDxwPkhhcyBwdWJsaXNoZWQgYm9va3M6PC9wPlxuICA8c3Bhbj57eyBwdWJsaXNoZWRCb29rc01lc3NhZ2UgfX08L3NwYW4+XG48L3RlbXBsYXRlPiIsImltcG9ydC1tYXAuanNvbiI6IntcbiAgXCJpbXBvcnRzXCI6IHtcbiAgICBcInZ1ZVwiOiBcImh0dHBzOi8vc2ZjLnZ1ZWpzLm9yZy92dWUucnVudGltZS5lc20tYnJvd3Nlci5qc1wiXG4gIH1cbn0ifQ==)

Ở đây chúng ta đã khai báo một thuộc tính computed `publishedBooksMessage`. Hàm `computed()` nhận vào một hàm getter (hàm dùng để lấy giá trị), và giá trị được trả về là một **computed ref (tham chiếu)**. Tương tự như các ref thông thường, bạn có thể truy cập giá trị của nó thông qua `publishedBooksMessage.value`. Khi dùng trong template, `ref`sẽ được unwrap tự động nên bạn có thể tham chiếu tới nó mà không cần `.value`.

Một thuộc tính computed sẽ tự động theo dõi các phụ thuộc có tính reactive. Vue biết rằng giá trị của `publishedBooksMessage` phụ thuộc vào `author.books`, nên nó sẽ cập nhật mọi ràng buộc vào `publishedBooksMessage` khi `author.books` thay đổi.

Xem thêm: [Typing Computed](/guide/typescript/composition-api.html#typing-computed) <sup class="vt-badge ts" />

</div>

## Computed Caching vs Methods

Bạn có thể đã để ý rằng chúng ta có thể đạt được kết quả tương tự bằng cách dùng một lệnh gọi phương thức trong biểu thức:

```vue-html
<p>{{ calculateBooksMessage() }}</p>
```

<div class="options-api">

```js
// in component
methods: {
  calculateBooksMessage() {
    return this.author.books.length > 0 ? 'Yes' : 'No'
  }
}
```

</div>

<div class="composition-api">

```js
// in component
function calculateBooksMessage() {
  return author.books.length > 0 ? 'Yes' : 'No'
}
```

</div>

Thay vì một thuộc tính computed, chúng ta có thể định nghĩa một hàm tương tự để làm một phương thức. Và kết quả cuối cùng, hai cách tiếp cận đều cho kết quả tương tự. Tuy nhiên sự khác biệt là **các thuộc tính computed được cache dựa trên những sự phụ thuộc có tính reactive của nó.** Một thuộc tính computed sẽ chỉ được tính lại khi một số sự phụ thuộc của nó thay đổi. Điều này có nghĩa là miễn `author.books` không thay đổi, thì mọi lần truy cập vào `publishedBooksMessage` đều ngay lập tức trả về kết quả đã được tính toán trước đó mà không chạy lại hàm getter.

Điều này có nghĩa là thuộc tính computed dưới đây sẽ không bao giờ được cập nhật, bởi vì `Date.now()` không phải là một sự phụ thuộc có tính reactive.

<div class="options-api">

```js
computed: {
  now() {
    return Date.now()
  }
}
```

</div>

<div class="composition-api">

```js
const now = computed(() => Date.now())
```

</div>

Trong khi đó, một lệnh gọi phương thức sẽ **luôn** chạy hàm đó bất cứ khi nào việc render lại xảy ra.

Tại sao chúng ta cần cache? Giả sử ta có một thuộc tính computed là `list`, thuộc tính này đòi hỏi lặp qua một mảng khổng lồ và thực hiện rất nhiều phép tính. Tiếp theo đó, chúng ta có thể có những thuộc tính computed khác phụ thuộc vào `list`. Nếu không có cache, chúng ta sẽ phải thực thi hàm getter của `list` nhiều hơn mức cần thiết rất nhiều! Trong những trường hợp bạn không muốn cache, hãy sử dụng phương thức thay vì thuộc tính computed.

## Thuộc tính computed có thể ghi

Mặc định thì những thuộc tính computed là chỉ đọc (chỉ có getter). Nếu bạn cố ghi giá trị mới vào một thuộc tính computed, bạn sẽ nhận được một cảnh báo runtime. Trong các trường hợp hãn hữu bạn cần một thuộc tính computed có thể ghi, bạn có thể cung cấp cả getter và setter cho nó:

<div class="options-api">

```js
export default {
  data() {
    return {
      firstName: 'John',
      lastName: 'Doe'
    }
  },
  computed: {
    fullName: {
      // getter
      get() {
        return this.firstName + ' ' + this.lastName
      },
      // setter
      set(newValue) {
        // Note: we are using destructuring assignment syntax here.
        [this.firstName, this.lastName] = newValue.split(' ')
      }
    }
  }
}
```

Giờ khi bạn chạy `this.fullName = 'John Doe'`, setter sẽ được gọi rồi `this.firstName` và `this.lastName` sẽ được cập nhật tương ứng.

</div>

<div class="composition-api">

```vue
<script setup>
import { ref, computed } from 'vue'

const firstName = ref('John')
const lastName = ref('Doe')

const fullName = computed({
  // getter
  get() {
    return firstName.value + ' ' + lastName.value
  },
  // setter
  set(newValue) {
    // Note: we are using destructuring assignment syntax here.
    [firstName.value, lastName.value] = newValue.split(' ')
  }
})
</script>
```

Giờ khi bạn chạy `fullName.value = 'John Doe'`, setter sẽ được gọi rồi `firstName` vả `lastName` sẽ được cập nhật tương ứng.

</div>

## Lời khuyên khi dùng thuộc tính computed 

### Getter không nên có hiệu ứng phụ

Điều quan trọng cần phải nhớ là hàm getter chỉ nên thực hiện duy nhất một việc tính toán đơn thuần và không có hiệu ứng phụ. Ví dụ, đừng tạo một request đồng bộ hoặc thay đổi DOM bên trong một hàm getter! Hãy xem thuộc tính computed như một khai báo về cách để lấy giá trị dựa trên những giá trị khác – nó chỉ có trách nhiệm tính toán và trả về giá trị đó mà thôi. Ở phần sau của hướng dẫn, chúng ta sẽ thảo luận về cách để thực hiện một hiệu ứng phụ dựa trên sự thay đổi của state bằng [watcher](./watchers). 

### Tránh thay đổi các giá trị đã tính

Giá trị được trả về từ một thuộc tính computed là trạng thái được suy luận ra. Hãy xem nó như một snapshot (ảnh chụp) tạm thời – mỗi khi các trạng thái mà nó phụ thuộc bị thay đổi, thì một snapshot mới được tạo ra. Việc thay đổi một snapshot là không hợp lý, vậy một giá trị được trả về bởi computed nên được xem là chỉ đọc và không bao giờ bị thay đổi – thay vào đó, hãy cập nhật trạng thái mà nó phụ thuộc để kích hoạt những tính toán mới.
