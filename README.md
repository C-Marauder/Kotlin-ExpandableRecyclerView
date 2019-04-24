# 基于RecyclerView和DataBinding封装的折叠列表

[ ![Download](https://api.bintray.com/packages/xqy666666/maven/ExpandableRecyclerView/images/download.svg?version=1.0.0) ](https://bintray.com/xqy666666/maven/ExpandableRecyclerView/1.0.0/link)

## 依赖

`implementation 'com.xqy.expandablerecyclerview:ExpandableRecyclerView:1.0.0'`

## 使用

```
 val items = mutableListOf<String>()
            for (i in 0..20) {
                items.add("$i")
            }
  recyclerview.adapter = ExpandableAdapter.builder {
                groupLayout {
                    R.layout.item
                }
                headerLayout {
                    R.layout.item_test
                }
                getHeaderItemData {
                    "我是头部"
                }
                bindHeaderItemData<String> {
                    item, dataBinding ->  (dataBinding as ItemTestBinding).num = item
                }
                childLayout {
                    R.layout.item_child
                }

                groupItems {
                    items
                }

                childItems { position ->
                    mutableListOf("hahah", "ppppp", "建设大街世纪东方")

                }
                bindGroupItemData<String> { item, dataBinding ->
                    (dataBinding as ItemBinding).num = item
                }



                createChildViewHolder {
                    dataBinding, itemView ->  ChildViewHolder(dataBinding as ItemChildBinding,itemView)
                }
            }
```
<img src="https://github.com/xqy666666/Kotlin-ExpandableRecyclerView/blob/master/expand.gif" width="300" height="600"/>
