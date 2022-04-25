# Render theo điều kiện

<script setup>
import { ref } from 'vue'
const awesome = ref(true)
</script>

## `v-if`

Directive `v-if` dùng để render theo điều kiện một khối (block). Khối chỉ được render nếu biểu thức của directive trả về một giá trị đúng (truthy).

```vue-html
<h1 v-if="awesome">Vue is awesome!</h1>
```

## `v-else`

Bạn có thể sử dụng directive `v-else` để chỉ ra một "khối else" cho `v-if`:

```vue-html
<button @click="awesome = !awesome">Toggle</button>

<h1 v-if="awesome">Vue is awesome!</h1>
<h1 v-else>Oh no 😢</h1>
```

<div class="demo">
  <button @click="awesome = !awesome">Toggle</button>
  <h1 v-if="awesome">Vue is awesome!</h1>
  <h1 v-else>Oh no 😢</h1>
</div>

<div class="composition-api">

[Chạy thử](https://sfc.vuejs.org/#eyJBcHAudnVlIjoiPHNjcmlwdCBzZXR1cD5cbmltcG9ydCB7IHJlZiB9IGZyb20gJ3Z1ZSdcblxuY29uc3QgYXdlc29tZSA9IHJlZih0cnVlKVxuPC9zY3JpcHQ+XG5cbjx0ZW1wbGF0ZT5cbiAgPGJ1dHRvbiBAY2xpY2s9XCJhd2Vzb21lID0gIWF3ZXNvbWVcIj50b2dnbGU8L2J1dHRvbj5cblxuXHQ8aDEgdi1pZj1cImF3ZXNvbWVcIj5WdWUgaXMgYXdlc29tZSE8L2gxPlxuXHQ8aDEgdi1lbHNlPk9oIG5vIPCfmKI8L2gxPlxuPC90ZW1wbGF0ZT4iLCJpbXBvcnQtbWFwLmpzb24iOiJ7XG4gIFwiaW1wb3J0c1wiOiB7XG4gICAgXCJ2dWVcIjogXCJodHRwczovL3NmYy52dWVqcy5vcmcvdnVlLnJ1bnRpbWUuZXNtLWJyb3dzZXIuanNcIlxuICB9XG59In0=)

</div>
<div class="options-api">

[Chạy thử](https://sfc.vuejs.org/#eyJBcHAudnVlIjoiPHNjcmlwdD5cbmV4cG9ydCBkZWZhdWx0IHtcbiAgZGF0YSgpIHtcbiAgXHRyZXR1cm4ge1xuXHQgICAgYXdlc29tZTogdHJ1ZVxuICBcdH1cblx0fVxufVxuPC9zY3JpcHQ+XG5cbjx0ZW1wbGF0ZT5cbiAgPGJ1dHRvbiBAY2xpY2s9XCJhd2Vzb21lID0gIWF3ZXNvbWVcIj50b2dnbGU8L2J1dHRvbj5cblxuXHQ8aDEgdi1pZj1cImF3ZXNvbWVcIj5WdWUgaXMgYXdlc29tZSE8L2gxPlxuXHQ8aDEgdi1lbHNlPk9oIG5vIPCfmKI8L2gxPlxuPC90ZW1wbGF0ZT4iLCJpbXBvcnQtbWFwLmpzb24iOiJ7XG4gIFwiaW1wb3J0c1wiOiB7XG4gICAgXCJ2dWVcIjogXCJodHRwczovL3NmYy52dWVqcy5vcmcvdnVlLnJ1bnRpbWUuZXNtLWJyb3dzZXIuanNcIlxuICB9XG59In0=)

</div>

Một phần tử `v-else` phải theo ngay sau `v-if` hoặc `v-else-if`, nếu không nó sẽ không được chấp nhận.

## `v-else-if`

Như tên gọi cho thấy, `v-else-if` đóng vai trò là một "khối else if" cho `v-if`. Ta có thể viết nhiều `v-else-if` liên tiếp nhau:

```vue-html
<div v-if="type === 'A'">
  A
</div>
<div v-else-if="type === 'B'">
  B
</div>
<div v-else-if="type === 'C'">
  C
</div>
<div v-else>
  Not A/B/C
</div>
```

Tương tự `v-else`, một phần tử `v-else-if` phải theo ngay sau `v-if` hoặc `v-else-if`.

## `v-if` trên `<template>`

Vì là một directive, `v-if` phải được gắn với một phần tử duy nhất. Nhưng nếu ta muốn kích hoạt nhiều hơn một phần tử thì sao? Trong trường hợp này, ta có thể sử dụng `v-if` trên một phần tử `<template>`, đóng vai trò như một khối bọc (wrapper) vô hình. Kết quả render cuối cùng sẽ không bao gồm phần tử `<template>`.

```vue-html
<template v-if="ok">
  <h1>Title</h1>
  <p>Paragraph 1</p>
  <p>Paragraph 2</p>
</template>
```

`v-else` và `v-else-if` cũng có thể sử dụng trên `<template>`.

## `v-show`

Một lựa chọn khác cho việc render một phần tử theo điều kiện là directive `v-show`. Cách sử dụng gần như hoàn toàn tương tự:

```vue-html
<h1 v-show="ok">Hello!</h1>
```

Điểm khác nhau căn bản là một phần tử với `v-show` sẽ luôn được render và nằm trong DOM; `v-show` chỉ kích hoạt thuộc tính CSS `display` của phần tử.

`v-show` không hỗ trợ `<template>` và không hoạt động với `v-else`.

## `v-if` vs `v-show`

`v-if` là hiển thị có điều kiện "thật" vì nó đảm bảo các xử lý sự kiện và component con bên trong khối điều kiện bị hủy bỏ và tái tạo trong quá trình kích hoạt.

Đồng thời, `v-if` cũng **lười biếng** (lazy): nếu điều kiện trả về giá trị sai (falsy) khi hiển thị lần đầu, nó sẽ không làm gì cả - khối điều kiện sẽ không được render cho đến khi điều kiện trở thành đúng lần đầu tiên.

Để so sánh, `v-show` đơn giản hơn nhiều – phần tử luôn được render bất kể điều kiện ban đầu và được kích hoạt bằng CSS.

Nói tóm lại, `v-if` có chi phí kích hoạt cao hơn, trong khi `v-show` có chi phí render lần đầu cao hơn. Vì vậy `v-show` phù hợp nếu bạn cần kích hoạt cái gì đó thường xuyên, và `v-if` phù hợp nếu điều kiện gần như không thay đổi trong quá trình chạy (runtime).

## `v-if` with `v-for`

::: warning Chú ý
**Không nên** dùng `v-if` và `v-for` trên cùng một phần tử do sự ưu tiên ngầm định. Tham khảo [hướng dẫn cách viết](/style-guide/rules-essential.html#avoid-v-if-with-v-for) để biết thêm chi tiết.
:::

Khi dùng cả `v-if` và `v-for` trên cùng một phần tử, `v-if` sẽ được xử lý trước. Xem [hướng dẫn về render danh sách](list#v-for-with-v-if) để biết thêm chi tiết.
