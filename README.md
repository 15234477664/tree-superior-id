# tree-superior-id
树形结构数据 已知某一子节点 一次向上获取所有父节点

```js
var res = [{
    code: 1,
    name: "湖北省",
    children: [{
        code: 1,
        name: "武汉市",
        children: [{
            code: 1,
            name: "汉阳区",
            children: [{
                code: 1,
                name: "水上分局1"
            }]
        }, {
            code: 1,
            name: "武昌区",
            children: [{
                code: 1,
                name: "水上分局2"
            }]
        }, {
            code: 1,
            name: "汉口区",
            children: [{
                code: 1,
                name: "水上分局3"
            }]
        }]
    }, {
        code: 1,
        name: "十堰市",
        children: [{
            code: 1,
            name: "郧阳区",
            children: [{
                code: 1,
                name: "安阳镇"
            }]
        }, {
            code: 1,
            name: "茅箭区",
            children: [{
                code: 1,
                name: "小川乡"
            }]
        }]
    }]
}]


function treeFindPath (tree, func, path = []) {
  if (!tree) return []
  for (const data of tree) {
    // 这里按照你的需求来存放最后返回的内容吧
    path.push(data.name)
    if (func(data)) return path
    if (data.children) {
      const findChildren = treeFindPath(data.children, func, path)
      if (findChildren.length) return findChildren
    }
    path.pop()
  }
  return []
}

treeFindPath(res, data=> data.name==='水上分局')
```
