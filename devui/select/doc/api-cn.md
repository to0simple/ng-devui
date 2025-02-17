# 如何使用

在 module 中引入：

```typescript
import { SelectModule } from 'ng-devui/select';
```

在页面中使用:

```html
<d-select [options]="options" [(ngModel)]="value"></d-select>
```

## d-select

### d-select 参数

|                       参数                       |                        类型                         |                       默认                       | 说明                                                                                                                                                                                | 跳转 Demo                                                   |全局配置项| 
| :----------------: | :----------------------------------------------: | :-------------------------------------------------: | :----------------------------------------------: | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------- |
|                     options                      |                       `array`                       |                        []                        | 可选, 和 searchFn 互斥，两者必须有且只有一个。下拉选项资源`string` `object`                                                                                                         | [基本用法](demo#basic-usage)                                |
|                     isSearch                     |                      `boolean`                      |                      false                       | 可选,是否支持过滤搜索                                                                                                                                                               | [使用对象](demo#object-filter)                              |
|                   scrollHight                    |                      `string`                       |                     '300px'                      | 可选,下拉菜单高度,建议使用 px 作为高度单位                                                                                                                                          |
|                highlightItemClass                |                      `string`                       |                    'bg-grey'                     | 可选,下拉高亮 css                                                                                                                                                                   |
|                    filterKey                     |                      `string`                       |                        --                        | 当传入资源 options 类型为 object 时,必选,针对传入资源 options 的每项对应字段做过滤操作                                                                                              | [使用对象](demo#object-filter)                              |
|                     multiple                     |                      `boolean`                      |                      false                       | 可选,是否支持多选                                                                                                                                                                   | [自定义搜索功能](demo#custom-search)                        |
|                   isSelectAll                    |                      `boolean`                      |                      false                       | 可选,是否显示全选                                                                                                                                                                   | [全选下拉选项](demo#select-all)                             |
|                     readonly                     |                      `boolean`                      |                       true                       | 可选,是否可以输入                                                                                                                                                                   | [标签化](demo#labelization)                                 |
|                       size                       |                      `string`                       |                        ''                        | 可选,下拉选框尺寸,有三种选择`'lg'`,`''`,`'sm'`                                                                                                                                      | [基本用法](demo#basic-usage)                                |
|                     disabled                     |                      `boolean`                      |                      false                       | 可选,是否禁用下拉框                                                                                                                                                                 | [禁用](demo#disabled)                                       |
|                   placeholder                    |                      `string`                       |             'Please Input keywords'              | 可选,输入框的 placeholder                                                                                                                                                           | [基本用法](demo#basic-usage)                                |
|                searchPlaceholder                 |                      `string`                       |                        ''                        | 可选,搜索功能输入框的 placeholder                                                                                                                                                   | [自定义搜索功能](demo#custom-search)                        |
|                     searchFn                     |                    `(term: string) => Observable<Array<{id: number, option: any}>>`                     |                        --                       | 可选,搜索函数,当需要自定义下拉选择过滤规则时可以使用                                                                                                                                | [自定义搜索功能](demo#custom-search)                        |
|                   valueParser                    |                     `Function`                      |                        --                        | 可选,决定选择框文字如何显示,默认显示 filterKey 字段或者本身的值                                                                                                                     |
|                    formatter                     |                     `Function`                      |                        --                        | 可选,决定下拉框每项文字如何显示,默认显示 filterKey 字段或者本身的值                                                                                                                 |
|                    direction                     |               `'up'\|'down'\|'auto'`                |                        ''                        | 可选,下拉选框弹出方向,有三种选择`'up'`,`'down'`,`'auto'`                                                                                                                                | [禁用](demo#disabled)                                       |
|                     overview                     |                      `string`                       |                     'border'                     | 可选,决定选择框样式显示,默认有边框`'border'`,`'underlined'`                                                                                                                         | [基本用法](demo#basic-usage)                                |
|                  enableLazyLoad                  |                      `boolean`                      |                      false                       | 可选,是否支持数据懒加载，用于滚动到底部时动态请求数据                                                                                                                               | [虚拟滚动 或 懒加载](demo#lazy-load-virtual-scroll)         |
|                   extraConfig                    |                      `object`                       |                       N/A                        | 可选, 可输入配置项 参考示例                                                                                                                                                         | [自定义模板](demo#select-template)                          |
|             extraConfig.labelization             |                      `object`                       |                       N/A                        | 可选, 标签化多选结果的配置项,参考示例                                                                                                                                               | [标签化](demo#labelization)                                 |
|         extraConfig.labelization.enable          |                      `boolean`                      |                      false                       | 可选下的必填参数, 是否启用标签化,使用必须置为 true,参考示例                                                                                                                         | [标签化](demo#labelization)                                 |
|        extraConfig.labelization.overflow         |                      `string`                       |                        ''                        | 可选, 多个标签超出容器时候的预处理行为,值为`'normal' \| 'scroll-y' \| 'multiple-line' \| 'string'` 对应默认隐藏,纵向滚动、自动变多行和自定义类                                      | [标签化](demo#labelization)                                 |
|   extraConfig.labelization.containerMaxHeight    |                      `string`                       |                     '1.8em'                      | 可选, 限制容器最高高度。 多行模式下默认不限制高度,单行模式下默认为 1.8em                                                                                                            |
| ~~extraConfig.labelization.containnerMaxHeight~~ |                      `string`                       |                     '1.8em'                      | 已废弃, 限制容器最高高度。 多行模式下默认不限制高度,单行模式下默认为 1.8em, 请使用`extraConfig.labelization.containerMaxHeight`                                                     |
|      extraConfig.labelization.labelMaxWidth      |                      `string`                       |                      '100%'                      | 可选, 限制标签宽度,默认值为行宽的 100%                                                                                                                                            |
|       extraConfig.enableFocusFirstFilteredOption  |                      `boolean`                     |                       --                        | 可选, 在多选情况下，允许用户搜索后按回车操作结果的第一个选项，没有结果则关闭下拉列表                                                                                    |                    |
|       extraConfig.selectedItemWithTemplate       |                      `object`                       |                       N/A                        | 可选,在单选情况下,显示选项使用了 template 的情况下,顶部选中的内容是否也以 template 展示,参考示例                                                                                    | [自定义模板](demo#select-template)                          |
|   extraConfig.selectedItemWithTemplate.enable    |                      `boolean`                      |                        --                        | 可选下的必填参数, 是否启用选中项使用模板,使用必须置为 true,参考示例                                                                                                                 | [自定义模板](demo#select-template)                          |
|                optionDisabledKey                 |                      `string`                       |                        ''                        | 可选,禁用单个选项;当传入资源 options 类型为`Object`,比如设置为`'disabled'`,则当对象的 disabled 属性为 true 时,该选项将禁用;当设置为`''`时不禁用单个选项                             | [禁用](demo#disabled)                                       |
|                optionImmutableKey                |                      `string`                       |                        ''                        | 可选,禁用单个选项;当传入资源 options 类型为`Object`,比如设置为`'immutable'`,则当对象的 immutable 属性为 true 时,该选项将禁被禁止变更;当设置为`''`时不生效                           | [禁用](demo#disabled)                                       |
|               noResultItemTemplate               |                    `TemplateRef`                    |                        --                        | 可选,没有匹配项的展示结果                                                                                                                                                           |
|                keepMultipleOrder                 |                      `string`                       |                  'user-select'                   | 可选,`'user-select' \| 'origin'`,配置多选的时候是否维持原数组排序还是用户选择的顺序排序,默认是用户顺序                                                                              | [设置已选项顺序源数组顺序或选中顺序](demo#multi-keep-order) |
|                customViewTemplate                |                    `TemplateRef`                    |                        --                        | 可选,支持自定义区域显示内容定制,可以使用 choose 来选择某项,choose 需要传两个必填参数,第一个为选择的选项,第二个为选项在列表的 index 值,event 参数选填,若不填请自行处理冒泡,详见 demo | [自定义区域](demo#custom-area)                              |
|               customViewDirection                |       `'bottom' \| 'right'\| 'left'\| 'top'`        |                     'bottom'                     | 可选, customViewTemplate 所处的相对下拉列表的位置                                                                                                                                   | [自定义区域方向和选中](demo#custom-area-direction)          |
|                   appendToBody                   |                      `boolean`                      |                      false                       | 可选, true 会被附加到 body                                                                                                                                                          | [附着到 Body 上](demo#append-to-body)                       |
|              appendToBodyDirections              | `Array<AppendToBodyDirection \| ConnectedPosition>` | `['rightDown', 'leftDown', 'rightUp', 'leftUp']` | 可选，方向数组优先采用数组里靠前的位置，AppendToBodyDirection 和 ConnectedPosition 请参考 dropdown                                                                                  | [自定义区域方向和选中](demo#custom-area-direction)          |
|                    autoFocus                     |                      `boolean`                      |                      false                       | 可选，是否自动聚焦                                                                                                                                                                  |
|                  toggleOnFocus                   |                      `boolean`                      |                      false                       | 可选，是否 focus 自动展开下拉列表                                                                                                                                                   |
|                      width                       |                      `number`                       |                        --                        | 可选，搭配 appendToBody 使用，设置下拉宽度                                                                                                                                          | [自定义区域方向和选中](demo#custom-area-direction)          |
|                  virtualScroll                   |                      `boolean`                      |                      false                       | 可选，是否虚拟滚动，大数据量场景试用                                                                                                                                                | [虚拟滚动 或 懒加载](demo#lazy-load-virtual-scroll)         |
|                    allowClear                    |                      `boolean`                      |                      false                       | 可选, 配置是否允许清空选值，仅单选场景适用                                                                                                                                          | [允许清空值](demo#allow-clear-value)                        |
|                inputItemTemplate                 |                    `TemplateRef`                    |                        --                        | 可选,自定义模板，若传入，会忽略 ContentChild                                                                                                                                        |                                                             |
|               ~~~notAutoScroll~~~                |                      `boolean`                      |                      false                       | `待改名`~~~可选，自动聚焦的时候，自动滚动到 select 位置~~~                                                                                                                          |
|                 templateItemSize                 |                      `number`                       |                      false                       | `待完善`可选，模板单条高度, appendToBody 必须为 true                                                                                                                                |
|                loadingTemplateRef                |                 `TemplateRef<any>`                  |                        --                        | 可选，自定义 loading 模板                                                                                                                                                           | [虚拟滚动 或 懒加载](demo#lazy-load-virtual-scroll)         |
|  showAnimation   |             `boolean`              |                                 true                                  |  可选，是否开启动画 |   | ✔ |

### d-select 事件

|     事件     |                              类型                               | 说明                                                                                                                                   | 跳转 Demo                                           |
| :----------: | :-------------------------------------------------------------: | :------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------- |
| valueChange  |                 `EventEmitter<Array<any>\|any>`                 | 可选,输出函数,当选中某个选项后,将会调用此函数,参数为当前选择项的值                                                                   |
| toggleChange |                     `EventEmitter<boolean>`                     | 可选,输出函数,下拉打开关闭 toggle 事件                                                                                                 | [异步加载显示加载中](demo#async-loading)            |
|   loadMore   | `EventEmitter<{instance: SelectComponent, event: ScrollEvent}>` | 懒加载触发事件，配合`enableLazyLoad`使用，使用`$event.instance.loadFinish()`结束本次加载, event 为懒加载监听的滚动事件，参考 dLazyLoad | [虚拟滚动 或 懒加载](demo#lazy-load-virtual-scroll) |

注意： 使用 appendToBody 后需要在有滚动条的地方使用`cdkScrollable`

```terminal
npm install @angular/cdk --save
```

```TypeScript
import { ScrollDispatchModule } from '@angular/cdk/scrolling';

@NgModule({
  imports: [
    // ...
    ScrollDispatchModule,
    // ...
  ]
})
```

```html
<div class="foo-bar-baz" cdkScrollable>
  <!--滚动条容器的其他内容-->
</div>
```
