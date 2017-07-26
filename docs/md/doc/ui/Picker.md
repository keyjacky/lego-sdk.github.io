# Picker

Picker 组件为 WebView 提供一个多功能的选择器，该选择器实际上是调用原生的 UIPickerView 和 Android Picker 实现的。

你可以为 Picker 定义标题、多列选择值、每列的标题等属性。

* 最多支持三列的数据

## RequestParams

String      title            - 选择器顶部标题

String[]    columnTitles     - 各列的标题

String[][]  columns          - 各列的值数组

String[]    defaultValues    - 各列的默认值

## 联动 Picker 的 RequestParams

Boolean     isColumnsRelated - 设为 true 时，开启联动 Picker
Item[]      columns          - 树状数值

Item = Object {
    title: "标题", 
    item: Item[],            
}

## ResponseParams

String[]    selectedValues   - 各列的选中值

## Sample

```
var message = JSMessage.newMessage()
message.moduleName = "UI.Picker"
message.requestParams = {
    title: "会议时间",
    columns: [
        ["A", "B", "C", "D", "E", "F", "G", "H"],
        ["A", "B", "C", "D", "E", "F", "G", "H"],
        ["A", "B", "C", "D", "E", "F", "G", "H"],
    ],
    columnTitles: ["日期", "开始时间", "结束时间"],
    defaultValues: ["C", "E", "H"],
}
message.call(function(meta, res){
                console.log(res.selectedValues);
                });
```

## Sample 联动

```
var message = JSMessage.newMessage()
message.moduleName = "UI.Picker"
message.requestParams = {
    isColumnsRelated: true,
    title: "地区",
    columns: [
        {
            "title": "广东省",
            "item": [
                {
                    "title": "广州市",
                    "item": [
                        {
                            "title": "天河区",
                        },
                        {
                            "title": "越秀区",
                        },
                        {
                            "title": "荔湾区",
                        },
                        {
                            "title": "大学城",
                        }
                    ]
                },
                {
                    "title": "汕头市",
                    "item": [
                        {
                            "title": "澄海区",
                        },
                        {
                            "title": "潮安区",
                        }
                    ]
                }
            ]
        },
        {
            "title": "海南省",
            "item": [
                {
                    "title": "海口市",
                    "item": [
                        {
                            "title": "美兰区",
                        },
                        {
                            "title": "秀英港",
                        }
                    ]
                },
                {
                    "title": "三亚市",
                    "item": [
                        {
                            "title": "市区",
                        },
                        {
                            "title": "亚龙湾",
                        }
                    ]
                }
            ]
        }
    ],
    columnTitles: ["省", "市", "区"],
    defaultValues: ["广东省", "汕头市", "潮安区"],
}
message.call(function (meta, res) {
    JSConsole.log(res.selectedValues);
});
```