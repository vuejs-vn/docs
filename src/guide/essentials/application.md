# Tạo ứng dụng Vue

## Application instance

Mội ứng dụng Vue được khởi động bằng cách tạo một **application instance** (thực thể của ứng dụng, từ đây ta cũng gọi tắt là "app instance") với hàm [`createApp`](/api/application#createapp):

```js
import { createApp } from 'vue'

const app = createApp({
  /* tùy chọn cho component gốc */
})
```

## Component gốc

Object mà ta đưa vào hàm `createApp` trên đây thực ra là một _component_. Mỗi app Vue yêu cầu một "component gốc," component này có thể chứa các component con khác.

Nếu sử dụng Single-File Component, thường thì ta import component gốc từ một file khác:  

```js
import { createApp } from 'vue'
// import component gốc "App" từ một single-file component
import App from './App.vue'

const app = createApp(App)
```

Tuy đa số các ví dụ trong hướng dẫn này chỉ cần một component, các app trong thực tế thường được sắp xếp thành một cây component lồng nhau và có thể tái sử dụng. Đơn cử, cây component của một app Todo có thể có dạng như sau:  

```
App (component gốc)
├─ TodoList
│  └─ TodoItem
│     ├─ TodoDeleteButton
│     └─ TodoEditButton
└─ TodoFooter
   ├─ TodoClearButton
   └─ TodoStatistics
```

Trong các phần sau của hướng dẫn, chúng ta sẽ bàn về cách định nghĩa và soạn thảo nhiều component cùng lúc. Nhưng trước tiên, chúng ta sẽ tập trung vào những gì xảy ra bên trong một component đơn lẻ.

## Mount một app

Một app instance sẽ không render ra gì hết cho đến khi phương thức `.mount()` của nó được gọi. Phương thức này nhận vào một tham số "container," là một phần tử DOM hoặc một selector:

```html
<div id="app"></div>
```

```js
app.mount('#app')
```

Nội dung của component gốc của một ứng dụng sẽ được render bên trong phần tử container. Phần tử container không được xem là một phần của app. 

Bạn nên gọi phương thức `.mount()` sau khi cài đặt toàn bộ cấu hình và đăng kí các asset. Đồng thời, lưu ý rằng giá trị trả về của nó, không giống như các phương thức đăng kí asset, là một instance của component gốc thay vì của app. 

### Template cho component gốc trong DOM

Khi sử dụng Vue mà không thông qua bước build, chúng ta có thể viết trực tiếp template (bản mẫu) cho component gốc bên trong container được mount:

```html
<div id="app">
  <button @click="count++">{{ count }}</button>
</div>
```

```js
import { createApp } from 'vue'

const app = createApp({
  data() {
    return {
      count: 0
    }
  }
})

app.mount('#app')
```

Vue sẽ tự động dùng `innerHTML` của container làm template nếu component gốc không có tùy chọn `template` sẵn.

## Cấu hình cho app

App instance có một object `.config`, cho phép chúng ta cấu hình một số các tùy chọn ở tầng app, ví dụ như định nghĩa một trình xử lí lỗi (error handler) để thu thập các lỗi được ném ra từ các component bên dưới:

```js
app.config.errorHandler = (err) => {
  /* xử lí lỗi */
}
```

App instance cũng cung cấp một số phương thức để đăng kí asset ở phạm vi app (app-scoped), ví dụ như đăng kí một component:

```js
app.component('TodoDeleteButton', TodoDeleteButton)
```

Đoạn code trên đây đăng kí component `TodoDeleteButton` để sử dụng ở bất kì nơi nào trong app. Chúng ta sẽ bàn thêm về việc đăng kí component và các loại asset khác trong các phần sau của hướng dẫn này. Bạn cũng có thể xem danh sách đầy đủ của các instance API trong mục [tham chiếu API](/api/application). 

Nhớ áp dụng toàn bộ các cấu hình cho app trước khi gọi `.mount()`!

## Nhiều app instance cùng lúc

API `createApp` cho phép nhiều app Vue tồn tại trên cùng một trang, mỗi app có phạm vi riêng dành cho cấu hình và asset toàn cục của app đó:

```js
const app1 = createApp({
  /* ... */
})
app1.mount('#container-1')

const app2 = createApp({
  /* ... */
})
app2.mount('#container-2')
```

Nếu bạn đang sử dụng Vue để hỗ trợ thêm cho HTML render từ phía server (server-rendered HTML) và chỉ cần Vue điều khiển một số phạm vi cụ thể trên một trang web lớn, nên tránh việc sử dụng chỉ một app Vue cho toàn bộ trang. Thay vào đó, tạo nhiều app Vue riêng lẻ và mount các app này trên các phần tử DOM cần thiết.
