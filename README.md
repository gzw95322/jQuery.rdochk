# jQuery.rdochk
Jquery radio&checkbox模拟（esmodule版）

> **注意：**基于es6实现，目前只在webpack打包后才能正常使用。

## 调用

```html
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <title>Document</title>
    <script src="https://cdn.bootcss.com/jquery/1.8.3/jquery.min.js"></script>
  </head>
  <body>
    <div id="msgTypeTpl"></div>
    <script>
      $(function () {
        var data = [
        { label: "全部", value: "-1" },
        { label: "2", value: 0 },
        { label: "3", value: 1 },
        { label: "4", value: 2 },
        { label: "5", value: 3 },
        { label: "6", value: 4 }
    ];
        $("#msgTypeTpl").rdochk({
        type: "checkbox",
        data: data,
        value: "",
        allCheckedValue: "-1",
        allCheckedUse: "children",
        inputName: "infoTypeList",
        className: "",
        valueKey: "value",
        labelKey: "label",
        tpl: function(item, index) {
            return `
            <li
            class="rdochk-list-item${item.selected ? " active" : ""}"
            data-id="${item[this.valueKey]}"
            data-idx="${index}">
            <i class="iconfont icon-unchecked"><span class="ie-only">&#xe628;</span></i>
            <i class="iconfont icon-checked"><span class="ie-only">&#xe7b8;</span></i>
            ${item[this.labelKey]}
            </li>`;
        }
    });
      });
    </script>
  </body>
</html>

```



## 参数

| 参数            | 类型            | 默认值     | 注释                                                         |
| --------------- | --------------- | ---------- | ------------------------------------------------------------ |
| type            | String          | "checkbox" | 单选radio,多选checkbox, 默认多选                             |
| data            | Array           | []         | 元数据                                                       |
| value           | Array           | []         | 默认值, 单选时为string, 多选时为array                        |
| inputName       | String          | "chk"      | input 名称                                                   |
| valueKey        | String          | "id"       | value的key名字                                               |
| labelKey        | String          | "name"     | label的key名字                                               |
| className       | String          | ""         | 额外的样式class                                              |
| childrenKey     | String          | "children" | children的key名字                                            |
| placeholder     | String          | "请输入"   | placeholder                                                  |
| allCheckedValue | Boolean         | false      | 全选的id值, 没有全选时为false                                |
| allCheckedUse   | String          | "children" | 全选时返回什么值, all返回全选的值和子值, -1只返回全选的值, children只返回子值 |
| tpl             | Function/String | ""         | 自定义数据模板                                               |
| callBack        | Function        | value, ele | 回调，返回已选值, 和当前的dom节点                            |
