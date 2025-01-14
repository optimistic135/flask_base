# Flask_base

### 简单说明

1. 项目结构

```
D:.
├─models
│  └─download_pic             #图片保存到本地的目录
│  └─Picture_AI               #图片AI接口
│  └─Editting_AI.py           #编辑AI接口
│  └─Inspiration_AI.py        #灵感AI接口
│  └─Package_AI               #包装AI接口
└─test_image                  #测试图片
└─app.py
└─environment.yaml            #conda环境
└─requirements.txt            #python依赖项
└─README.md
└─test.http                   #测试的请求(已完善，vscode需要安装REST Client插件, 直接点击send request)
```

### 运行项目

1. 创建虚拟环境

```cmd
conda env create -f environment.yaml
```

2. 进入虚拟环境

```cmd
conda activate big_create
```

2. 安装flask等依赖

```cmd
pip install -r requirements.txt
```

3. 启动！

```cmd
python app.py
```

___

## Interface Infomation

## 接口列表

接口请求头均为`multipart/form-data`

|  接口  | 说明 |
|------ |----- |
|[/api/package_ai](#package)| 处理包装Ai部分|
|[/api/pic_ai/area_change](#pic/area) | 图片AI/区域换色|
|[/api/pic_ai/color_change](#pic/color) | 图片AI/一键换色|
|[/api/pic_ai/reference_change](#pic/reference) |图片AI/参考换色 |
|[/api/pic_ai/text_change](#pic/text) | 图片AI/文本换色|
|[/api/inspire](#inspire) | 灵感Ai|
|[/api/edit_ai](#edit) | 编辑i|

***

## 错误码列表

|  错误码  | 说明 |
|------ |----- |
|   0   | 正确 |
|   1   | 错误 |
|   2   | 参数错误|

## 接口详情

* **<font size=5><span id="package">包装AI</span></font>**

  * 接口地址：`/api/package_ai`
  * 返回格式：`json`
  * 请求方式：`POST`
  * 接口备注：接受`提示词`,`参考图片`,`图片蒙版`，`模型`参数，返回多视图，和模型文件（`.obj`）
  * 请求参数说明：

    | 名称        | 类型  | 必填 | 说明        |
    |-----------  |------|------|------------ |
    | description | string | true | 提示词        |
    | reference   | file | true | 参考        |
    | mask        | file | true | 蒙版        |
    | model       | file | true | 模型        |

  * 返回参数说明：（根据后续具体的实现功能调整返回参数）

    | 名称          | 类型   | 说明         |
    |---------------|--------|--------------|
    | status           | int    |状态码       |
    | mutiply_pic   | file    | 多视图(可拼接成一张图片)   |
    | gen_model     | file    | 生成的模型文件   |
    | msg           | string    | 信息       |

  * JSON返回示例：（后续调整）

             {
                "status": 0,
                "date": {
                  "mutiply_pic": a.jpg,
                  "gen_model": a.obj, 
                  "color_setting":{
                      "material": a.mtl,
                      "col_pic": a.png
                  },
                  "msg": "successful to finish download",
                }
             }

* **<font size=5><span id="pic/cloor">图片AI/一键换色</span></font>**

  * 接口地址：`/api/pic_ai/color_change`
  * 返回格式：`json`
  * 请求方式：`POST`
  * 接口备注：接受`颜色`，`参考图片`参数，返回多视图，和模型文件（`.obj`）
  * 请求参数说明：

    | 名称        | 类型  | 必填 | 说明        |
    |-----------  |------|------|------------ |
    | color       | string | true | 颜色   |
    | reference   | file | true | 参考        |

  * 返回参数说明：
    * 同上接口的返回参数，后续根据具体实现调整
    * JSON返回示例：（后续调整）

             {
                "status": 0,
                "date": {
                  "mutiply_pic": a.jpg,
                  "gen_model": a.obj, 
                  "color_setting":{
                      "material": a.mtl,
                      "col_pic": a.png
                  },
                  "msg": ""
                }
             }

* **<font size=5><span id="pic/area">图片AI/区域换色</span></font>**

  * 接口地址：`/api/pic_ai/area_change`
  * 返回格式：`json`
  * 请求方式：`POST`
  * 接口备注：接受`颜色`，`参考图片`,`图片蒙版`参数，返回多视图，和模型文件（`.obj`）
  * 请求参数说明：

    | 名称        | 类型  | 必填 | 说明        |
    |-----------  |------|------|------------ |
    | color       | string | true | 颜色   |
    | reference   | file | true | 参考        |
    | mask        | file | true | 蒙版        |

  * 返回参数说明：
    * 同上接口的返回参数，后续根据具体实现调整
    * JSON返回示例：（后续调整）

             {
                "status": 0,
                "date": {
                  "mutiply_pic": a.jpg,
                  "gen_model": a.obj,
                  "color_setting":{
                      "material": a.mtl,
                      "col_pic": a.png
                  },
                  "msg": ""
                }
             }
* **<font size=5><span id="pic/text">图片AI/文本换色</span></font>**

  * 接口地址：`/api/pic_ai/text_change`
  * 返回格式：`json`
  * 请求方式：`POST`
  * 接口备注：接受`提示词`，`参考图片`,`图片蒙版`参数，返回多视图，和模型文件（`.obj`）
  * 请求参数说明：

    | 名称        | 类型  | 必填 | 说明        |
    |-----------  |------|------|------------ |
    | description | string | true | 提示词        |
    | reference   | file | true | 参考        |
    | mask        | file | true | 蒙版        |

  * 返回参数说明：
    * 同上接口的返回参数，后续根据具体实现调整
    * JSON返回示例：（后续调整）

             {
                "status": 0,
                "date": {
                  "mutiply_pic": a.jpg,
                  "gen_model": a.obj, 
                  "msg": ""
                }
             }

* **<font size=5><span id="pic/reference">图片AI/参考换色</span></font>**

  * 接口地址：`/api/pic_ai/reference_change`
  * 返回格式：`json`
  * 请求方式：`POST`
  * 接口备注：接受`参考图片1`,`参考图片2`参数，返回多视图，和模型文件（`.obj`）
  * 请求参数说明：

    | 名称        | 类型  | 必填 | 说明        |
    |-----------  |------|------|------------ |
    | image      | file | true | 图片        |
    | reference   | file | true | 参考        |

  * 返回参数说明：
    * 同上接口的返回参数，后续根据具体实现调整
    * JSON返回示例：（后续调整）

             {
                "status": 0,
                "date": {
                  "mutiply_pic": a.jpg,
                  "gen_model": a.obj, 
                  "color_setting":{
                      "material": a.mtl,
                      "col_pic": a.png
                  },
                  "msg": ""
                }
             }

* **<font size=5><span id="inspire">灵感AI</span></font>**

  * 接口地址：`/api/inspire`
  * 返回格式：`json`
  * 请求方式：`POST`
  * 接口备注：接受`参考图片`,`图片蒙版`参数，返回多视图
  * 请求参数说明：

    | 名称        | 类型  | 必填 | 说明        |
    |-----------  |------|------|------------ |
    | reference   | file | true | 参考        |
    | mask        | file | true | 蒙版        |

  * 返回参数说明：（根据后续具体的实现功能调整返回参数）

    | 名称          | 类型   | 说明         |
    |---------------|--------|--------------|
    | status           | int    |状态码       |
    | mutiply_pic   | file    | 多视图(可拼接成一张图片)   |
    | msg           | string    | 信息       |

  * JSON返回示例：（后续调整）

             {
                "status": 0,
                "date": {
                  "mutiply_pic": a.jpg,
                  "color_setting":{
                      "material": a.mtl,
                      "col_pic": a.png
                  },
                  "msg": ""
                }
             }

* **<font size=5><span id="edit">编辑AI</span></font>**

  * 接口地址：`/api/edit_ai`
  * 返回格式：`json`
  * 请求方式：`POST`
  * 接口备注：接受`参考图片`，返回`原图`，`结果图`
  * 请求参数说明：

    | 名称        | 类型  | 必填 | 说明        |
    |-----------  |------|------|------------ |
    | reference   | file | true | 参考        |

  * 返回参数说明：（根据后续具体的实现功能调整返回参数）

    | 名称          | 类型   | 说明         |
    |---------------|--------|--------------|
    | status           | int    |状态码       |
    | raw_pic   | file    | 多视图(可拼接成一张图片)   |
    | new_pic   | file    | 多视图(可拼接成一张图片)   |
    | msg           | string    | 信息       |

  * JSON返回示例：（后续调整）

             {
                "status": 0,
                "date": {
                  "raw_pic": a.jpg,
                  "new_pic": b.jpg,
                  "msg": ""
                }
             }
