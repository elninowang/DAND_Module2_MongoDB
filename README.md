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


### 使用 Match 和 Project 运算符

match_project.py

问题描述

写一个回答以下问题的聚合查询：

对于巴西利亚时区的用户，哪些用户发推次数不低于 100 次，哪些用户的关注者数量最多？

以下提示将帮助你解决这一问题：

你可以在每个推特的用户对象的“time_zone”字段中找到时区。
你可以在“statuses_count”字段中找到每个用户的发推数量。
注意，你需要创建“followers”、“screen_name”和“tweets”字段。

只需修改“make_pipeline”函数，使其创建并返回一个聚合管道，该管道可以传递到 MongoDB 聚合函数中。和这节课中的示例一样，聚合管道应该是一个包含一个或多个字典对象的列表。如果不熟悉语法，请参阅这节课中的示例。

你的代码将根据我们提供的 MongoDB 实例运行。如果你想在本地机器上运行代码，你需要安装 MongoDB 并下载和插入数据集。要了解 MongoDB 设置和数据集方面的说明，请参阅课程资料。

请注意，你在此处使用的数据集是这节课的示例中使用的推特数据集的简略版本。如果你尝试运行我们在课程示例中运行过的同一查询，结果可能不同。

聚合框架运算符文档

注意：在当前版本的 pymongo (3.0) 中，聚合运算返回的是游标对象。为了看到所返回的元素，你可以在游标对象上进行迭代（比如使用 for 循环），并逐个输出元素。在本地计算机上操作时，请记住这一点。

示例推文：

```javascript
{
    "_id" : ObjectId("5304e2e3cc9e684aa98bef97"),
    "text" : "First week of school is over :P",
    "in_reply_to_status_id" : null,
    "retweet_count" : null,
    "contributors" : null,
    "created_at" : "Thu Sep 02 18:11:25 +0000 2010",
    "geo" : null,
    "source" : "web",
    "coordinates" : null,
    "in_reply_to_screen_name" : null,
    "truncated" : false,
    "entities" : {
        "user_mentions" : [ ],
        "urls" : [ ],
        "hashtags" : [ ]
    },
    "retweeted" : false,
    "place" : null,
    "user" : {
        "friends_count" : 145,
        "profile_sidebar_fill_color" : "E5507E",
        "location" : "Ireland :)",
        "verified" : false,
        "follow_request_sent" : null,
        "favourites_count" : 1,
        "profile_sidebar_border_color" : "CC3366",
        "profile_image_url" : "http://a1.twimg.com/profile_images/1107778717/phpkHoxzmAM_normal.jpg",
        "geo_enabled" : false,
        "created_at" : "Sun May 03 19:51:04 +0000 2009",
        "description" : "",
        "time_zone" : null,
        "url" : null,
        "screen_name" : "Catherinemull",
        "notifications" : null,
        "profile_background_color" : "FF6699",
        "listed_count" : 77,
        "lang" : "en",
        "profile_background_image_url" : "http://a3.twimg.com/profile_background_images/138228501/149174881-8cd806890274b828ed56598091c84e71_4c6fd4d8-full.jpg",
        "statuses_count" : 2475,
        "following" : null,
        "profile_text_color" : "362720",
        "protected" : false,
        "show_all_inline_media" : false,
        "profile_background_tile" : true,
        "name" : "Catherine Mullane",
        "contributors_enabled" : false,
        "profile_link_color" : "B40B43",
        "followers_count" : 169,
        "id" : 37486277,
        "profile_use_background_image" : true,
        "utc_offset" : null
    },
    "favorited" : false,
    "in_reply_to_user_id" : null,
    "id" : NumberLong("22819398300")
}
```

### 使用 Unwind 运算符

unwind.py

问题描述

对于这道练习，我们回到城市 infobox 数据集。我们希望你能回答以下问题：印度的哪个地区包括的城市最多？（确保将城市计数存储在叫做“count”的字段中；请参阅脚本末尾的声明。）

首先，使用我们提出的以下示例问题的答案：谁在推特中提到的用户数最多？

对于城市数据，需要注意的一点是：“isPartOf”字段包含一个地区数组，可以在其中查找城市。请参阅下面的讲师注释中的示例文档。

只需修改“make_pipeline”函数，使其创建并返回一个聚合管道，该管道可以传递到 MongoDB 聚合函数中。和这节课中的示例一样，聚合管道应该是一个包含一个或多个字典对象的列表。如果不熟悉语法，请参阅这节课中的示例。

你的代码将根据我们提供的 MongoDB 实例运行。如果你想在本地机器上运行代码，你需要安装 MongoDB 并下载和插入数据集。要了解 MongoDB 设置和数据集方面的说明，请参阅课程资料。

请注意，你在此处使用的数据集是这节课的示例中使用的城市集合的简略版本。如果你尝试运行我们在课程示例中运行过的同一查询，结果可能不同。

管道聚合运算符文档

注意：在当前版本的 pymongo (3.0) 中，聚合运算返回的是游标对象。为了看到所返回的元素，你可以在游标对象上进行迭代（比如使用 for 循环），并逐个输出元素。在本地计算机上操作时，请记住这一点。

这是一个示例文档：
```javascript
{
    "_id" : ObjectId("52fe1d364b5ab856eea75ebc"),
    "elevation" : 1855,
    "name" : "Kud",
    "country" : "India",
    "lon" : 75.28,
    "lat" : 33.08,
    "isPartOf" : [
        "Jammu and Kashmir",
        "Udhampur district"
    ],
    "timeZone" : [
        "Indian Standard Time"
    ],
    "population" : 1140
}
```

### 使用推送

push.py

问题描述

$push 与 $addToSet 相似。区别在于 $push 会将所有值（而不是唯一值）整合到数组中。

通过聚合查询查找出每个用户的推特数量。在相同的 $group 阶段，使用 $push 数出每个用户的所有推特文本数量。仅数出推特数量在前五名的用户。

最后的文档应该仅包含以下字段：

- "_id"（用户的帐号名）， 
- "count"（用户的推文数量），
- "tweet_texts"（用户的推文列表）。

只需修改“make_pipeline”函数，使其创建并返回一个聚合管道，该管道可以传递到 MongoDB 聚合函数中。和这节课中的示例一样，聚合管道应该是一个包含一个或多个字典对象的列表。如果不熟悉语法，请参阅这节课中的示例。

你的代码将根据我们提供的 MongoDB 实例运行。如果你想在本地机器上运行代码，你需要安装 MongoDB 并下载和插入数据集。要了解 MongoDB 设置和数据集方面的说明，请参阅课程资料。

请注意，你在此处使用的数据集是这节课的示例中使用的推特数据集的简略版本。如果你尝试运行我们在课程示例中运行过的同一查询，结果可能不同。
组聚合运算符文档

注意：在当前版本的 pymongo (3.0) 中，聚合运算返回的是游标对象。为了看到所返回的元素，你可以在游标对象上进行迭代（比如使用 for 循环），并逐个输出元素。在本地计算机上操作时，请记住这一点。

示例推文：

```javascript
{
    "_id" : ObjectId("5304e2e3cc9e684aa98bef97"),
    "text" : "First week of school is over :P",
    "in_reply_to_status_id" : null,
    "retweet_count" : null,
    "contributors" : null,
    "created_at" : "Thu Sep 02 18:11:25 +0000 2010",
    "geo" : null,
    "source" : "web",
    "coordinates" : null,
    "in_reply_to_screen_name" : null,
    "truncated" : false,
    "entities" : {
        "user_mentions" : [ ],
        "urls" : [ ],
        "hashtags" : [ ]
    },
    "retweeted" : false,
    "place" : null,
    "user" : {
        "friends_count" : 145,
        "profile_sidebar_fill_color" : "E5507E",
        "location" : "Ireland :)",
        "verified" : false,
        "follow_request_sent" : null,
        "favourites_count" : 1,
        "profile_sidebar_border_color" : "CC3366",
        "profile_image_url" : "http://a1.twimg.com/profile_images/1107778717/phpkHoxzmAM_normal.jpg",
        "geo_enabled" : false,
        "created_at" : "Sun May 03 19:51:04 +0000 2009",
        "description" : "",
        "time_zone" : null,
        "url" : null,
        "screen_name" : "Catherinemull",
        "notifications" : null,
        "profile_background_color" : "FF6699",
        "listed_count" : 77,
        "lang" : "en",
        "profile_background_image_url" : "http://a3.twimg.com/profile_background_images/138228501/149174881-8cd806890274b828ed56598091c84e71_4c6fd4d8-full.jpg",
        "statuses_count" : 2475,
        "following" : null,
        "profile_text_color" : "362720",
        "protected" : false,
        "show_all_inline_media" : false,
        "profile_background_tile" : true,
        "name" : "Catherine Mullane",
        "contributors_enabled" : false,
        "profile_link_color" : "B40B43",
        "followers_count" : 169,
        "id" : 37486277,
        "profile_use_background_image" : true,
        "utc_offset" : null
    },
    "favorited" : false,
    "in_reply_to_user_id" : null,
    "id" : NumberLong("22819398300")
}
```

### Same 运算符

same.py

问题描述

在上一道练习中，我们查看了城市数据集，并询问印度的哪个地区包含的城市最多。在这道练习中，我们想请你回答另一个关于印度地区的相关问题。印度各个地区的平均人口数量是多少？你需要首先计算每个地区城市的平均人口数量，然后计算地区的平均人口数量。

提示：如果你想使用所有输入文档中的值汇集到一个群组阶段中，可以使用常量作为“_id”字段的值。例如：

{ "$group" : {"_id" : "India Regional City Population Average", ... }

只需修改“make_pipeline”函数，使其创建并返回一个聚合管道，该管道可以传递到 MongoDB 聚合函数中。和这节课中的示例一样，聚合管道应该是一个包含一个或多个字典对象的列表。如果不熟悉语法，请参阅这节课中的示例。

你的代码将根据我们提供的 MongoDB 实例运行。如果你想在本地机器上运行代码，你需要安装 MongoDB 并下载和插入数据集。要了解 MongoDB 设置和数据集方面的说明，请参阅课程资料。

请注意，你在此处使用的数据集是这节课的示例中使用的推特数据集的简略版本。如果你尝试运行我们在课程示例中运行过的同一查询，结果可能不同。

MongoDb 运算符文档

注意：在当前版本的 pymongo (3.0) 中，聚合运算返回的是游标对象。为了看到所返回的元素，你可以在游标对象上进行迭代（比如使用 for 循环），并逐个输出元素。在本地计算机上操作时，请记住这一点。

这是一个示例文档：
```javascript
{
    "_id" : ObjectId("52fe1d364b5ab856eea75ebc"),
    "elevation" : 1855,
    "name" : "Kud",
    "country" : "India",
    "lon" : 75.28,
    "lat" : 33.08,
    "isPartOf" : [
        "Jammu and Kashmir",
        "Udhampur district"
    ],
    "timeZone" : [
        "Indian Standard Time"
    ],
    "population" : 1140
}
```