# Cú pháp template

Vue sử dụng cú pháp template dựa trên HTML, cho phép bạn ràng buộc (bind) một cách minh bạch cấu trúc DOM được render với dữ liệu của đối tượng Vue bên dưới. Tất cả template của Vue đều là code HTML hợp lệ và có thể được parse những các trình duyệt và HTML parser tiểu chuẩn.

Bên dưới, Vue biên dịch các template thành code JavaScript được tối ưu cao. Kết hợp với hệ thống reactivity (phản ứng), Vue có thể xác định một cách thông mình số lượng tối thiểu các component cần phải render lại, và áp dụng số lượng tối thiểu các thao tác về DOM khi trạng thái của ứng dụng thay đổi.

Nếu bạn đã quen thuộc với khái niệm Virtual DOM và muốn sử dụng sức mạnh của JavaScript, bạn có thể [viết thẳng các hàm render](/guide/extras/render-function.html) cùng với JSX (không bắt buộc), thay vì sử dụng template. Tuy nhiên, hãy lưu ý rằng chúng (các hàm render) không thừa hưởng cùng mức độ tối ưu về thời gian biên dịch như template. 

## Nội suy văn bản

Hình thức ràng buộc dữ liệu cơ bản nhất là nội suy văn bản (text interpolation) sử dụng cú pháp "Mustache" ("ria mép" - hai dấu ngoặc nhọn):

```vue-html
<span>Thông điệp: {{ msg }}</span>
```

Thẻ mustache sẽ được thay thế bằng giá trị của thuộc tính `msg` từ component instance tương ứng, và cũng sẽ được cập nhật bất cứ khi nào thuộc tính này thay đổi.

## HTML thuần túy

Cú pháp mustache sẽ thông dịch dữ liệu thành văn bản thuần (plain text) chứ không phải HTML. Để xuất được HTML, bạn sẽ cần đến directive [`v-html`](/api/built-in-directives.html#v-html).

```vue-html
<p>Sử dụng nội suy văn bản: {{ rawHtml }}</p>
<p>Sử dụng directive v-html: <span v-html="rawHtml"></span></p>
```

<script setup>
  const rawHtml = '<span style="color: red">Màu đỏ</span>'
</script>

<div class="demo">
  <p>Sử dụng nội suy văn bản: {{ rawHtml }}</p>
  <p>Sử dụng directive v-html: <span v-html="rawHtml"></span></p>
</div>

Chúng ta bắt gặp điều gì mới ở đây. Đó là thuộc tính `v-html` mà bạn đang nhìn thấy ở trên được gọi là **directive**. Directive có tiền tố (prefix) là `v-` để chỉ ra rằng chúng là thuộc tính đặc biệt của Vue, và như bạn có thể đã đoán được, chúng áp dụng những hành vi reactive đặc biết đối với DOM được render. Về cơ bản chúng ta đang nói "giữ nguyên HTML bên trong phần tử này luôn được cập nhật với `rawHtml` trên instance hiện tại."

Nội dung bên trong `span` sẽ được thay thế bởi giá trị của thuộc tính `rawHhtml`, và được thông dịch thành HTML thuần - những ràng buộc dữ liệu sẽ bị bỏ qua. Chú ý rằng bạn không thể sử dụng `v-html` để biên soạn template partial, bởi vì Vue không phải là string-based template engine. Thay vào đó, component được xem là đơn vị nên tảng cho việc tái sử dụng và biên tập UI. 
 
:::warning Cảnh báo bảo mật
Render HTML động tùy tiện trên website của bạn có thể rất nguy hiểm vì nó dễ dàng dẫn đến [các lỗ hỏng XSS](https://en.wikipedia.org/wiki/Cross-site_scripting). Vì thế chỉ dùng `v-html` với các nội dung đáng tin tưởng, **đừng bao giờ** dùng với các nội dung được người dùng cung cấp. 
:::

## Attribute Bindings

Mustaches cannot be used inside HTML attributes. Instead, use a [`v-bind` directive](/api/built-in-directives.html#v-bind):

```vue-html
<div v-bind:id="dynamicId"></div>
```

The `v-bind` directive instructs Vue to keep the element's `id` attribute in sync with the component's `dynamicId` property. If the bound value is `null` or `undefined`, then the attribute will be removed from the rendered element.

### Shorthand

Because `v-bind` is so commonly used, it has a dedicated shorthand syntax:

```vue-html
<div :id="dynamicId"></div>
```

Attributes that start with `:` may look a bit different from normal HTML, but it is in fact a valid character for attribute names and all Vue-supported browsers can parse it correctly. In addition, they do not appear in the final rendered markup. The shorthand syntax is optional, but you will likely appreciate it when you learn more about its usage later.

> For the rest of the guide, we will be using the shorthand syntax in code examples, as that's the most common usage for Vue developers.

### Boolean Attributes

[Boolean attributes](https://html.spec.whatwg.org/multipage/common-microsyntaxes.html#boolean-attributes) are attributes that can indicate true / false values by its presence on an element. For example, [`disabled`](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes/disabled) is one of the most commonly used boolean attributes.

`v-bind` works a bit differently in this case:

```vue-html
<button :disabled="isButtonDisabled">Button</button>
```

The `disabled` attribute will be included if `isButtonDisabled` has a [truthy value](https://developer.mozilla.org/en-US/docs/Glossary/Truthy). It will also be included if the value is an empty string, maintaining consistency with `<button disabled="">`. For other falsy values the attribute will be omitted.

### Dynamically Binding Multiple Attributes

If you have a JavaScript object representing multiple attributes that looks like this:

<div class="composition-api">

```js
const objectOfAttrs = {
  id: 'container',
  class: 'wrapper'
}
```

</div>
<div class="options-api">

```js
data() {
  return {
    objectOfAttrs: {
      id: 'container',
      class: 'wrapper'
    }
  }
}
```

</div>

You can bind them to a single element by using `v-bind` without an argument:

```vue-html
<div v-bind="objectOfAttrs"></div>
```

## Using JavaScript Expressions

So far we've only been binding to simple property keys in our templates. But Vue actually supports the full power of JavaScript expressions inside all data bindings:

```vue-html
{{ number + 1 }}

{{ ok ? 'YES' : 'NO' }}

{{ message.split('').reverse().join('') }}

<div :id="`list-${id}`"></div>
```

These expressions will be evaluated as JavaScript in the data scope of the current component instance.

In Vue templates, JavaScript expressions can be used in the following positions:

- Inside text interpolations (mustaches)
- In the attribute value of any Vue directives (special attributes that start with `v-`)

### Expressions Only

Each binding can only contain **one single expression**, so the following will **NOT** work:

```vue-html
<!-- this is a statement, not an expression: -->
{{ var a = 1 }}

<!-- flow control won't work either, use ternary expressions -->
{{ if (ok) { return message } }}
```

### Calling Functions

It is possible to call a component-exposed method inside a binding expression:

```vue-html
<span :title="toTitleDate(date)">
  {{ formatDate(date) }}
</span>
```

:::tip
Functions called inside binding expressions will be called every time the component updates, so they should **not** have any side effects, such as changing data or triggering asynchronous operations.
:::

### Restricted Globals Access

Template expressions are sandboxed and only have access to a [restricted list of globals](https://github.com/vuejs/core/blob/main/packages/shared/src/globalsWhitelist.ts#L3). The list exposes commonly used built-in globals such as `Math` and `Date`.

Globals not explicitly included in the list, for example user-attached properties on `window`, will not be accessible in template expressions. You can, however, explicitly define additional globals for all Vue expressions by adding them to [`app.config.globalProperties`](/api/application.html#app-config-globalproperties).

## Directives

Directives are special attributes with the `v-` prefix. Vue provides a number of [built-in directives](/api/built-in-directives.html), including `v-html` and `v-bind` which we have introduced above.

Directive attribute values are expected to be single JavaScript expressions (with the exception of `v-for`, `v-on` and `v-slot`, which will be discussed in their respective sections later). A directive's job is to reactively apply updates to the DOM when the value of its expression changes. Take [`v-if`](/api/built-in-directives.html#v-if) as an example:

```vue-html
<p v-if="seen">Now you see me</p>
```

Here, the `v-if` directive would remove / insert the `<p>` element based on the truthiness of the value of the expression `seen`.

### Arguments

Some directives can take an "argument", denoted by a colon after the directive name. For example, the `v-bind` directive is used to reactively update an HTML attribute:

```vue-html
<a v-bind:href="url"> ... </a>

<!-- shorthand -->
<a :href="url"> ... </a>
```

Here `href` is the argument, which tells the `v-bind` directive to bind the element's `href` attribute to the value of the expression `url`. In the shorthand, everything before the argument (i.e. `v-bind:`) is condensed into a single character, `:`.

Another example is the `v-on` directive, which listens to DOM events:

```vue-html
<a v-on:click="doSomething"> ... </a>

<!-- shorthand -->
<a @click="doSomething"> ... </a>
```

Here the argument is the event name to listen to: `click`. `v-on` is one of the few directives that also have a corresponding shorthand, with its shorthand character being `@`. We will talk about event handling in more detail too.

### Dynamic Arguments

It is also possible to use a JavaScript expression in a directive argument by wrapping it with square brackets:

```vue-html
<!--
Note that there are some constraints to the argument expression,
as explained in the "Dynamic Argument Expression Constraints" section below.
-->
<a v-bind:[attributeName]="url"> ... </a>

<!-- shorthand -->
<a :[attributeName]="url"> ... </a>
```

Here `attributeName` will be dynamically evaluated as a JavaScript expression, and its evaluated value will be used as the final value for the argument. For example, if your component instance has a data property, `attributeName`, whose value is `"href"`, then this binding will be equivalent to `v-bind:href`.

Similarly, you can use dynamic arguments to bind a handler to a dynamic event name:

```vue-html
<a v-on:[eventName]="doSomething"> ... </a>

<!-- shorthand -->
<a @[eventName]="doSomething">
```

In this example, when `eventName`'s value is `"focus"`, `v-on:[eventName]` will be equivalent to `v-on:focus`.

#### Dynamic Argument Value Constraints

Dynamic arguments are expected to evaluate to a string, with the exception of `null`. The special value `null` can be used to explicitly remove the binding. Any other non-string value will trigger a warning.

#### Dynamic Argument Syntax Constraints

Dynamic argument expressions have some syntax constraints because certain characters, such as spaces and quotes, are invalid inside HTML attribute names. For example, the following is invalid:

```vue-html
<!-- This will trigger a compiler warning. -->
<a :['foo' + bar]="value"> ... </a>
```

If you need to pass a complex dynamic argument, it's probably better to use a [computed property](./computed.html), which we will cover shortly.

When using in-DOM templates (templates directly written in an HTML file), you should also avoid naming keys with uppercase characters, as browsers will coerce attribute names into lowercase:

```vue-html
<a :[someAttr]="value"> ... </a>
```

The above will be converted to `:[someattr]` in in-DOM templates. If your component has a `someAttr` property instead of `someattr`, your code won't work.

### Modifiers

Modifiers are special postfixes denoted by a dot, which indicate that a directive should be bound in some special way. For example, the `.prevent` modifier tells the `v-on` directive to call `event.preventDefault()` on the triggered event:

```vue-html
<form @submit.prevent="onSubmit">...</form>
```

You'll see other examples of modifiers later, [for `v-on`](./event-handling.html#event-modifiers) and [for `v-model`](./forms.html#modifiers), when we explore those features.

And finally, here's the full directive syntax visualized:

![directive syntax graph](./images/directive.png)

<!-- https://www.figma.com/file/BGWUknIrtY9HOmbmad0vFr/Directive -->
