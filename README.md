# BookSourceRepository

This is just a library of books on the code cloud.

仓库地址：https://raw.githubusercontent.com/YuSheng821/2333/master/chuner.json


---
### 书源制作
准备工作，需了解基础的Html/CSS/JavaScript内容，以及Jsoup选择器功能。

参考内容：[Jsoup选择器文档](https://jsoup.org/apidocs/org/jsoup/select/Selector.html) 和 [Jsoup调试神器](https://try.jsoup.org)
#### 搜索
书源必须具有搜索功能，填充入上一步的json中如下：

| 属性 | 含义 | 讲解 |
| :-: | :-: | --- |
| link | 地址 | ${key}代表搜索关键词，搜索时自动替换为用户输入的词； @post-> 表明后续使用POST方式传递参数，如果是GET方式不需要特殊声明，例如 http://search.com?key=${key} 意味key使用GET方式请求内容 |
| list | 结果 | 通过Jsoup选择结果元素 |

##### 书源属性讲解
- name ：书源名字
- version ：版本号，100即1.0.0
- category : 类别，0（出版）、1（网文）、2（轻小说）、3（综合）
- url ：来源链接（真实有效）
- charset ：字符集 utf-8 gbk gbk2312
- metadata： 元数据（每个子属性支持多个匹配，适应不同场景，比如排行榜或搜索）
    - name： 书名
    - author： 作者
    - cover：封面
    - summary： 摘要
    - category： 分类，例如：玄幻，武侠，连载等
    - status：状态（选填），完结 或 连载
    - update：更新时间（选填）（不填将无法检查更新）
    - lastChapter：更新章节（选填）（不填将无法检查更新）
    - link： 书籍详情地址
    - catalog：目录地址（不填视为目录与详情同一个地址）
- catalog： 目录
    - list：章节列表
    - orderBy：排序方式 0（分卷正序章节正序）1（分卷倒序章节倒序）2（分卷正序章节倒序）3（分卷倒序章节正序）
    - booklet：分卷（选填）
        - name：分卷名
        - list：章节列表
    - chapter： 章节
        - name：章节名
        - link：章节链接
- content：内容
    - text： 文本
    - next": {
        - link: 下页标签
        - text: 下页字符
    - filter：内容过滤（数组）
- search：搜索
    - link：链接
    - list：列表
- rank：排行榜（可选）
    - link：链接（数组）
        - name：名字
        - link：链接
    - list：列表
    - page：分页
        - index：起始索引
        - limit：单页数量
        - begin：起始页面拼接字符
        - next：下一页拼接字符
