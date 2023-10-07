# 将微信读书划线和笔记同步到Notion


本项目通过Github Action每天定时同步微信读书划线到Notion。

预览效果：https://book.malinkang.com


注意：请不要在Page里面添加自己的笔记，有新的笔记的时候会删除原笔记重新添加。

## 使用

1. star本项目
2. fork这个工程
3. 获取微信读书的Cookie
    * 浏览器打开 https://weread.qq.com/
    * 微信扫码登录确认，提示没有权限忽略即可
    * 按F12进入开发者模式，依次点 Network -> Doc -> Headers-> cookie。复制 Cookie 字符串;
        *  选择网络
        *  点击一下 一本书说任意内容
        *  在下方会出现一个名称，类型：`document`就是文件格式，点击之后就会出现`标头`对应上面的Headers
        *  在标头里面下拉找对应的cookie,具体位置在·请求标头·内部
4. 获取NotionToken
    * 浏览器打开https://www.notion.so/my-integrations
    * 点击New integration 输入name提交
    * 点击show，然后copy
    * 具体的图示![get-notiontoken](https://github.com/Xiaoshizi1024/weread_to_notion/assets/32703518/0ce81920-be6c-4b17-917c-3be2c3e7a1b9)

5. 复制[这个Notion模板](https://malinkang.notion.site/a7794117392d4625ace722f78742afca?v=0a9551b0702649fa9913ff4f3758ace0)，删掉所有的数据，并点击右上角设置，Connections添加你创建的Integration。

6. 获取NotionDatabaseID
    * 打开Notion数据库，点击右上角的Share，然后点击Copy link
    * 获取链接后比如 https://www.notion.so/malinkang/1b78f0fd0d03484caa00154285ffec0c?v=7ed7e3fbe69043a28d2847e76f075d99&pvs=4 中间的1b78f0fd0d03484caa00154285ffec0c就是DatabaseID
7. 在Github的Secrets中添加以下变量
    * 打开你fork的工程，点击Settings->Secrets and variables->New repository secret
    * 添加以下变量
        * WEREAD_COOKIE
        * NOTION_TOKEN
        * NOTION_DATABASE_ID

