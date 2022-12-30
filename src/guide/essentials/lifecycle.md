# Lifecycle Hooks

Mỗi Vue component instance khi được tạo ra đều trải qua một loạt các bước khởi tạo, ví dụ như là nó cần thiết lập quan sát dữ liệu (data observation), biên dịch template, mount instance đó ra DOM, và cập nhật DOM mỗi khi dữ liệu thay đổi. Đồng thời, nó cũng chạy các hàm được gọi là lifecycle hook để chúng ta có cơ hội chạy code của mình ở một số giai đoạn nhất định.

## Đăng ký Lifecycle Hooks

VD, <span class="composition-api">`onMounted`</span><span class="options-api">`mounted`</span> hook có thể sử dụng để chạy code sau khi component đã kết thúc render lần đầu và tạo các DOM node:

<div class="composition-api">

```vue
<script setup>
import { onMounted } from 'vue'

onMounted(() => {
  console.log(`the component is now mounted.`)
})
</script>
```

</div>
<div class="options-api">

```js
export default {
  mounted() {
    console.log(`the component is now mounted.`)
  }
}
```

</div>

Ngoài ra còn có các hook khác được gọi ở các giai đoạn khác nhau trong vòng đời của instance, trong đó thường được sử dụng nhất đó là <span class="composition-api">[`onMounted`](/api/composition-api-lifecycle.html#onmounted), [`onUpdated`](/api/composition-api-lifecycle.html#onupdated), and [`onUnmounted`](/api/composition-api-lifecycle.html#onunmounted).</span><span class="options-api">[`mounted`](/api/options-lifecycle.html#mounted), [`updated`](/api/options-lifecycle.html#updated), và [`unmounted`](/api/options-lifecycle.html#unmounted).</span>

<div class="options-api">
Tất cả các lifecycle hook được gọi với `this` context sẽ trỏ đến instance hiện tại đang được gọi. Lưu ý rằng điều này có nghĩa là bạn nên tránh sử dụng arrow functions khi khai báo các lifecycle hook, vì như thế nó sẽ làm bạn không thể truy cập đến component instance qua `this` nếu như bạn làm như trên.

</div>

<div class="composition-api">

Khi gọi `onMounted`, Vue tự động liên kết callback function với component instance hiện tại. Đều này yêu cầu các hook này phải được đăng ký **đồng bộ** trong khi thiết lập component. VD, chúng ta không nên làm như thế này:

```js
setTimeout(() => {
  onMounted(() => {
    // this won't work.
  })
}, 100)
```

Lưu ý rằng điều này không có nghĩa là hàm phải được đặt bên trong `setup()` hoặc `<script setup>` - `onMounted()` có thể được gọi từ bên ngoài miễn rằng call stack là đồng bộ và bắt nguồn từ `setup()`.

</div>

## Lifecycle Diagram

Bên dưới là biểu đồ vòng đời của instance. Bạn không cần phải hiểu hết mọi thứ ngay bây giờ nhưng khi bạn tìm hiểu và xây dựng nhiều thứ thơn thì nó sẽ là một tài liệu tham khảo hữu ích.

![Component lifecycle diagram](./images/lifecycle.png)

<!-- https://www.figma.com/file/Xw3UeNMOralY6NV7gSjWdS/Vue-Lifecycle -->

Tham khảo <span class="composition-api">[Lifecycle Hooks API reference](/api/composition-api-lifecycle.html)</span><span class="options-api">[Lifecycle Hooks API reference](/api/options-lifecycle.html)</span> để biết thêm chi tiết tất cả các lifecycle hook và các trường hợp sử dụng tương ứng của chúng.
