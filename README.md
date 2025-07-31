# 优惠酒店专属助理|免费黄金周旅行路线规划

## 🔥 UPDATE：支持在线体验的网页版已上线：https://hotel.gqmg.com/plan/#gh ，体验有针对性优化。

## MCP server一句话简介

输入出发和目的地，时间，自动规划行程安排，输出高性价比和舒适优质两条优惠酒店路线。

## 🚀 特性

- 根据用户输入的出发城市和旅游目的地，规划途径城市，推荐两条酒店优惠路线，以及优惠住宿信息。
- 可以基于已规划的路线进行微调 update-hotel-quality 。
- 支持 sse 格式、支持 mcp 格式、支持 windsurf 调用。

## 📋 提示词示例

- 路线规划：
10-1到10-5国庆期间，深圳到厦门自驾游，每天游玩一个城市并住宿。请帮我规划酒店安排,提供酒店特色和选择理由.

- 更新酒店：
请提升线路1，第二天的酒店品质。

<img width="638" height="1650" alt="image" src="https://github.com/user-attachments/assets/299e366f-9ef8-48a7-961a-b091b5506589" />

详细演示：https://t.kainy.cn/jdmcp

## 📦 安装和配置

支持 sse 格式

```json
{
  "mcpServers": {
  "hotel": {
      "url": "https://hotel.gqmg.com/sse/"
    }
  }
}
```

也支持 mcp 格式

```json
{
  "mcpServers": {
  "hotel": {
      "url": "https://hotel.gqmg.com/mcp/"
    }
  }
}
```

windsurf 调用

```json
{
    "mcpServers": {
    "特惠酒店MCP": {
      "serverUrl": "https://hotel.gqmg.com/sse/"
    }
  }
}
```

## 🔧 工具列表2个工具

#### 工具名称:recommend-hotel-route

工具介绍:根据用户输入的行程途径城市，推荐两条酒店优惠路线

| 参数名 | 参数类型 |示例|  参数介绍|
| - | - | - | - |
| cities | array | ["深圳", "厦门"]|途径的城市列表 |
| [Array Item]                    | string |  | |
| startDate                       | string |2025-10-01|旅行开始日期，格式为YYYY-MM-DD |
| endDate                         | string | 2025-10-05|旅行结束日期，格式为YYYY-MM-DD |
| toJSON                          | boolean | false|是否直接返回JSON数据，如果为false则调用generate-travel-article生成旅游计划书 |

#### 工具名称:update-hotel-quality

工具介绍:为现有计划中某一天的酒店，更换为更高品质或更低价格的

| 参数名 | 参数类型 | 示例| 参数介绍 |
| - | - | - |-|
| dayIndex | number |0|  要更新的日期索引，从0开始 |
| planType                                      | string |性价比优先路线|  要更新的路线类型 |
| preferHigherQuality                           | boolean | true| 是否优先选择更高品质的酒店，false表示优先选择更低价格的酒店 |
| routeData                                     | string |```[]```|  之前生成的路线数据，JSON格式 |
| toJSON                                        | boolean | false| 是否直接返回JSON数据，如果为false则调用generate-travel-article生成旅游计划书 |


