# 完整配置
如上一章hello world的例子所示，`plugin.json`文件可以让你的插件与uTools无缝的结合在一起，下面我们列出了所有可能的配置项及注释供你参考：
```json
{
    "pluginName": "插件名称",
    "version": "0.0.1",
    "description": "插件描述",
    // 在uTools对应的位置显示
    "author": "开发者",
    // 如果配置了此项，用户点击`开发者`时，将在浏览器中打开此页面
    "homepage": "https://u.tools",
    // 入口文件，为空表示模板插件
    "main": "index.html",
    // 这是一个关键文件，你可以在此文件内调用uTools 、nodejs、electron提供的api
    "preload":"preload.js",
    // 此插件的图标，这是必须存在的，否则打包后将无法安装
    "logo": "logo.png",
    // 插件支持的平台（默认为全平台支持）
    "platform": ["win32", "darwin", "linux"],
    // 在开发模式下，可使用development配置替换 main、preload、logo 的值，在打包时，此字段会被删除
    "development": {
        "main": "",
        "preload": "",
        "logo": "",
        // 可单独指定打包目录（默认为plugin.json所在目录）
        "buildPath": ""
    },
    // 插件设置 (可选)
    "pluginSetting":{
        // 插件是否允许多开(默认不允许)，多开方式：分离插件后，再次创建
        "single": true,
        // 插件高度(可动态修改,但用户不能调整高度)
        "height": 0
    },
    /*
     * features 描述了当uTools主输入框内容产生变化时，此插件是否显示在搜索列表中
     * 一个插件可以有多个功能，一个功能可以提供多个命令供用户搜索
     */ 
    "features": [
        {
        	// 插件提供的某个功能(必须)
            "code": "uuid", 
            // 对此功能的说明，在搜索列表中出现
            "explain": "随机唯一值",
            // 功能图标, 相对路径 支持png、jpg、svg (可选)
            "icon": "res/xxxx.png",
            // 功能适配平台 ["win32", "darwin", "linux"] (可选)
            "platform": ["win32", "darwin", "linux"],
            "cmds":[
              // cmds 可以是简单的字符串, 搜索进入
              "uTools", "中文",
              
              // cmds 也可以是一个对象，匹配场景，通过匹配过滤
              {
                 // 类型，可能的值（img, files, regex, over）
                 "type": "img",
                 // 文字说明，在搜索列表中出现（必须）
                 "label": "图片匹配"
              },
              
              // files 实例
              {
                "type": "files",
                "label": "文件匹配",
                // 支持file或directory (可选)
                "fileType": "file",
                // 文件名称正则匹配  (可选)
                "match": "/xxx/",
                // 数量限制（不少于） (可选)
                "minLength": 1,
                // 数量限制（不多于） (可选)
                "maxLength": 1
              },
              
              // regex 实例
              {
                "type": "regex",
                "label": "文本正则匹配",
                // 正则表达式字符串
                "match":"/xxx/i",
                // 长度限制（主输入框中的字符不少于） (可选)
                "minLength": 1,
                // 长度限制（不多于） (可选)
                "maxLength": 1
            },
            
            // over 实例(当uTools主输入框中的关键字无任何匹配项时出现)
            {
                "type": "over",
                "label": "无匹配时",
                // 排除的正则 (可选)
                "exclude":"/xxx/i",
                // 长度限制（主输入框中的字符不少于） (可选)
                "minLength": 1,
                // 长度限制（不多于） (可选)
                "maxLength": 1
            },
            
            // window 实例(根据呼出uTools前的活动窗口匹配) 
            // ps: 可使用uTools`窗口信息`关键字查看窗口信息 
            {
                "type": "window",
                "label": "窗口动作",
                "match": {
                   // 应用 (可选)
                   "app": ["xxx.app", "xxx.exe"],
                   // 匹配窗口标题的正则 (有配置时应用也必须配置) (可选)
                   "title": "/xxxx/",
                   // 窗口类  Windows专有 (可选)
                   "class": ["xxx"]
                }
            }
          ] 
       }
    ]
}
```