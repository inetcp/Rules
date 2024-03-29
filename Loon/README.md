# ssid.js

该脚本可根据配置和SSID更改Loon的运行模式以及策略。  
可与软路由配合使用，当连接到软路由WIFI时自动将Loon切换至全局直连或将节点选为 DIRECT 且不影响广告过滤等。

## 配置项

- runningModel  
    切换Loon的运行模式。可选值如下：
    - "GlobalDirect"
    - "ByRule"
    - "GlobalProxy"

- selectPolicy  
    切换策略组，该项应为键值对的形式存在。

## 配置示例：

- 网络切换配置  
    ```json
    {
        "ssid_1": {
            "runningModel": "GlobalDirect",
            "selectPolicy": {
                "节点选择": "DIRECT",
                "Google": "节点选择"
            }
        },
        "ssid_2": {
            "runningModel": "GlobalDirect",
            "selectPolicy": {
                "节点选择": "DIRECT",
                "Google": "节点选择"
            }
        }
    }
    ```
    其中 `"节点选择": "DIRECT"` 若要切换到 DIRECT 需要 "节点选择" 中存在 DIRECT 选项

- 默认配置  
    ```json
    {
        "runningModel": "GlobalDirect",
        "selectPolicy": {
            "节点选择": "节点名称或其他策略名称",
            "Google": "节点选择"
        }
    }
    ```
    其中更改 `runningModel` 会导致Loon规则无效，若想规则保持运行则可以删除此项，如下：
    ```json
    {
        "selectPolicy": {
            "节点选择": "节点名称或其他策略名称",
            "Google": "节点选择"
        }
    }
    ```