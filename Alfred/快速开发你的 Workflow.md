## 最重要的三点
1. 触发源;
2. 执行动作;
3. 输出;

## 1. 出发源
### 1.1 快捷键
可以是某个 App中的某个快捷健来触发；
#### 1.2 可以是 alfred 中的某个快捷键

## 2. 执行动作
#### 2.1 Python脚本
Alfred 中我们通常使用xml/json 来将结果展示在 alfred的显示栏中;
```json
{
    "items": [
        {
            "title": "Title12",
            "subtitle": "SubTitle",
            "arg": "This is arg",
            "icon": {
                "type": "default",
                "path": "icon.png"
            }
        }
    ]
}

```

一个基础的测试 workflow 示例 , 这里就不推荐使用官方的 workflow包了，对于 python3 尚且不具备较好的兼容性; 
从 query 中取出参数， item 中 arg 会被塞入 query中，进入下个模块;  
``` python
import json
arr = '{query}'
def create_item(title, subtitle, arg="", icon=""):
    item = {}
    item['title'] = title
    item['subtitle'] = subtitle
    item['arg'] = arg
    item['icon'] = icon
    return item

items = []
items.append(create_item("Title" + arr, "SubTitle", "This is arg"))


result = {}
result['items'] = items
print(json.dumps(result))

```


## 3. Action 
![[../static/alfred_workflow_dev.png]]