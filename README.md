# DAND_Module2_MongoDB
用python使用MongoDB的学习程序

### 插入多个文档

insert.py

题目说明
请向 insert_autos 函数中添加一行代码，将汽车数据插入“autos”集合中。

process_file 函数返回的数据变量是一个字典列表，如上一个视频中展示的示例所示。
对于本课程中使用的 MongoDB 版本，请查看此页面，了解 pymongo 中的批量插入。

在正式版本 3.0 中，该过程有轻微改变（详见此页面）。因此，当你在本地计算机上操作时，请注意这一点。

### 查找保时捷

find_porsche.py

你的任务是完成“porsche_query”函数，尤其是查找出制造商字段为“Porsche”的所有汽车的查询。

只需修改“porsche_query”函数，因为我们仅对该函数进行评分。

你的代码将根据我们提供的 MongoDB 实例运行。

如果你想在本地机器上运行代码，你需要安装 MongoDB 并下载和插入数据集。要了解 MongoDB 设置和数据集方面的说明，请参阅课程资料，链接如下：https://www.udacity.com/wiki/ud032
你可以查看 example_car.json 文件（第二个文件选项卡），找到作为查询依据的正确字段。

### 准备数据

processing.py

问题描述

在此习题集中，你将处理另一种类型的 infobox 数据，审核、清理数据，并得出一种数据模型，将数据插入 MongoDB，然后对数据库运行一些查询。数据集中包含关于蛛形纲动物的数据。

对于这道练习，你的任务是解析文件，仅处理 FIELDS 字典中作为键的字段，并返回清理后的值字典列表。

你应该完成以下几个步骤：

- 根据 FIELDS 字典中的映射更改字典的键
- 删掉“rdf-schema#label”中的小括号里的多余说明，例如“(spider)”
- 如果“name”为“NULL”，或包含非字母数字字符，将其设为和“label”相同的值。
- 如果字段的值为“NULL”，将其转换为“None”
- 如果“synonym”中存在值，应将其转换为数组（列表），方法是删掉“{}”字符，并根据“|” 拆分字符串。剩下的清理方式将由你自行决定，例- 如删除前缀“*”等。如果存在单数同义词，值应该依然是列表格式。
- 删掉所有字段前后的空格（如果有的话）
- 输出结构应该如下所示：

```javascript
[ { 'label': 'Argiope',
    'uri': 'http://dbpedia.org/resource/Argiope_(spider)',
    'description': 'The genus Argiope includes rather large and spectacular spiders that often ...',
    'name': 'Argiope',
    'synonym': ["One", "Two"],
    'classification': {
                      'family': 'Orb-weaver spider',
                      'class': 'Arachnid',
                      'phylum': 'Arthropod',
                      'order': 'Spider',
                      'kingdom': 'Animal',
                      'genus': None
                      }
  },
  { 'label': ... , }, ...
]
```

### 向 MongoDB 插入数据

dbinsert.py

问题描述

完成 insert_data 函数，将数据插入 MongoDB。