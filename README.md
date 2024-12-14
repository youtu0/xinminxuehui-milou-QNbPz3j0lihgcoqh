
# 推荐一款轻量级且强大的 Elasticsearch GUI ： elasticvue


很多同学都是用过 Elasticsearch 的 GUI 工具 Kibana ，但 Kibana 相对比较重，这篇文章，笔者推荐推荐一款**轻量级**且**强大**的 Elasticsearch GUI ： **elasticvue** 。


![https://img2024.cnblogs.com/blog/2487169/202412/2487169-20241213173926265-540236274.png](https://img2024.cnblogs.com/blog/2487169/202412/2487169-20241213173926265-540236274.png)


# 1 下载安装


进入： [https://github.com/cars10/elasticvue/releases/tag/v1\.1\.0](https://github.com)


![https://img2024.cnblogs.com/blog/2487169/202412/2487169-20241213173914217-1012589345.png](https://img2024.cnblogs.com/blog/2487169/202412/2487169-20241213173914217-1012589345.png)


由于笔者使用的是 macOS，因此下载了对应的 .dmg 文件。


安装完成之后，点击图标，显示如下：


![https://img2024.cnblogs.com/blog/2487169/202412/2487169-20241213173922112-805279235.png](https://img2024.cnblogs.com/blog/2487169/202412/2487169-20241213173922112-805279235.png)


# 2 集群配置


点击 **「**添加ELASTICSEARCH集群**」**按钮 ，选择不同的验证验证方式（无需验证、用户名和密码、API key）。


![https://img2024.cnblogs.com/blog/2487169/202412/2487169-20241213173912830-1853811285.gif](https://img2024.cnblogs.com/blog/2487169/202412/2487169-20241213173912830-1853811285.gif)


点击**「**测试连接**」**，弹出成功提示后，连接即可。


![https://img2024.cnblogs.com/blog/2487169/202412/2487169-20241213173920096-1372876860.png](https://img2024.cnblogs.com/blog/2487169/202412/2487169-20241213173920096-1372876860.png)


如图，集群首页显示集群的节点信息、集群健康状况等。


首页第一栏目有很多的操作选项：**节点、分片、索引、搜索、 REST 、快照、配置**。


![https://img2024.cnblogs.com/blog/2487169/202412/2487169-20241213173925707-1301981029.gif](https://img2024.cnblogs.com/blog/2487169/202412/2487169-20241213173925707-1301981029.gif)


# 2 创建索引


在Elasticsearch中创建索引是一个相对简单的过程，可以通过发送HTTP `PUT` 请求来完成。


创建索引时，你可以定义索引的设置（settings）和映射（mappings）。


具体示例步骤如下：


**1\. 准备工作**


确保你已经安装并运行了 Elasticsearch，并且可以通过命令行工具（如 curl）、编程语言客户端，或者通过 Kibana 的 Dev Tools 控制台与之交互。


本节介绍 elasticvue 如何通过 GUI 界面与 ES 交互创建索引。


**2、设计一个例子索引**



```
PUT /assetstestdataresources.filecenter.directory
{
  "mappings": {
    "properties": {
      "dir_name": {
        "type": "text",
        "fields": {
          "keyword": {
           "type": "keyword"
          }
        }
      },
      "entity_type": {
        "type": "keyword"
      },
      "entity_id": {
        "type": "keyword"
      },
      "add_time": {
        "type": "date",
        "format": "yyyy-MM-dd HH:mm:ss||epoch_millis"
      },
      "u_time": {
        "type": "date",
        "format": "yyyy-MM-dd HH:mm:ss||epoch_millis"
      },
      "tags": {
        "type": "text",
        "fields": {
          "keyword": {
            "type": "keyword"
          }
        }
      }
    }
  }
}

```

在Elasticsearch (ES) 中，`PUT` 方法用于创建或更新索引、文档或设置 ，请求体包含了一个 `mappings` 部分，这用来定义索引中文档的结构和字段的数据类型。映射是索引内文档结构的蓝图，它告诉 Elasticsearch 如何处理和存储数据。


**3、Rest 界面创建索引**


点击 REST 按钮，将例子索引拷贝左侧文本框，点击发起请求后，右侧文本框会返回响应结果。


![https://img2024.cnblogs.com/blog/2487169/202412/2487169-20241213173923470-1963168239.png](https://img2024.cnblogs.com/blog/2487169/202412/2487169-20241213173923470-1963168239.png)


# 3 添加数据


我们可以使用 POST 命令添加索引数据，格式如下：



```
PUT //_doc/
{
  "field1": "value1",
  "field2": "value2",
  // 更多字段...
}

```

我们添加 1 条示例数据：



```
POST /assetstestdataresources.filecenter.directory/_doc/1
{
  "dir_name": "供应商:KHBH-20241016-0001",
  "entity_type": "info_supplier",
  "entity_id": "1",
  "add_time": "2024-11-06 10:59:00",
  "u_time": "2024-11-06 10:59:00",
  "tags": ["供应商", "2024年", "新合作"]
}


```

![https://img2024.cnblogs.com/blog/2487169/202412/2487169-20241213173920210-1833421719.png](https://img2024.cnblogs.com/blog/2487169/202412/2487169-20241213173920210-1833421719.png)


# 4 查看索引


点击索引栏目，进入示例索引，可以查看所有的索引数据，点击最右侧操作按钮，查看数据详情。


![https://img2024.cnblogs.com/blog/2487169/202412/2487169-20241213173920654-1191826447.gif](https://img2024.cnblogs.com/blog/2487169/202412/2487169-20241213173920654-1191826447.gif)




---


 本博客参考[悠兔机场官网订阅](https://5tutu.com)。转载请注明出处！
