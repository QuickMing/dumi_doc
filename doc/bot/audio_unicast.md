点播功能输出：
服务名：audio_unicast

点播返回示例:
```javascript
// 播放相声

{
    "data": {
        "directives": [
            {
                "header": {
                  "message_id": "14851538172760",
                  "name": "Play",
                  "namespace": "AudioPlayer"
                },
                "payload": {
                    "play_behavior": "REPLACE_ALL",
                    "audio_item": {
                        "audio_item_id": "55690041011",
                        "stream": {
                            "url": "http://fdfs.xmcdn.com/group3/M01/77/42/wKgDsVKMdDLCVKUUAIMXy99Q7Vo340.mp3",
                            "stream_format": "mp3",
                            "offset_ms": 0,
                            "token": "55690041011",
                            "progress_report_interval_ms": 50000
                        }
                    }
                }
            }
        ],
        "speech": {
            "type": "Text",
            "content": "播放郭德纲相声"
        },
        "resource": {
            "type": "unicast_ref",
            "data": {
                "api": {
                    "method": "GET",
                    "url": "http://s.xiaodu.baidu.com/v20161223/unicast/playlist?cuid=XXXX"
                }
            }
        },
        "views": {
            "type": "txt",
            "content": "郭德纲相声"
        }
    }
}
```


### 1、专辑列表
  * 接口地址：http://s.xiaodu.baidu.com/v20161223/unicast/albumlist
  * 请求方式：GET
  * 请求参数：

参数|类型|是否必须|备注
----|----|--------|----
category|int|是|分类ID
cuid|string|是|设备ID，设备的唯一标识
appid|string|是|appid,标识接入方
page|int|否|页码，默认为1
pagesize|int|否|每页数据量，默认为10
sort|string |否 |排序：热门：grade、最新：album_last_track_time(默认：热门) 
orderby |string |否 |倒序：desc, 正序 asc （默认：asc） 

分类ID|分类名称
-------|--------
1|相声
2|小说
3|公开课
4|诗歌
5|戏曲
6|段子
7|讲座
8|演讲
9|健康养生
11|有声书
12|资讯
13|历史
14|评书
15|广播剧
16|小品
17|故事
18|人文
20|脱口秀

返回格式：
```javascript
{
	 status: 0,
     code: "",
     data: 
        {
            "page" : 1,        //当前页
            "total_page" : 10,  //总页数
            "list" 
               [
					{
						"id":1,  //专辑ID
						"album_title":"逻辑思维",  //专辑名
						"include_track_count":100,  //节目总数
						"cover_url": 
						{
							"small":"http://fdfs.xmcdn.com/group3/M09/34/94/wKgDsVMUWC-i2BqxAALZkSLeN4o874_mobile_small.jpg",
      						"middle":"http://fdfs.xmcdn.com/group3/M09/34/94/wKgDsVMUWC-i2BqxAALZkSLeN4o874_mobile_meduim.jpg",
      						"large":"http://fdfs.xmcdn.com/group3/M09/34/94/wKgDsVMUWC-i2BqxAALZkSLeN4o874_mobile_large.jpg",
						},
						"play_count":188376,  //播放量
						"category_name":"资讯",  //分类
						"category_id":3,  //分类ID
						"update_time":"2017-03-03 10:09:18",  //更新时间
						"create_time":"2017-03-03 10:09:18",  //创建时间
						"source": "喜马拉雅",  //资源方
						"source_icon": "http://xxxx.xxx.xxx/xx/xx.jpg",  //资源方Icon
					},
					{
						"id":1,
						"album_title":"逻辑思维2",
						"include_track_count":160,
						"cover_url": 
						{							
						    "small":"http://fdfs.xmcdn.com/group3/M09/34/94/wKgDsVMUWC-i2BqxAALZkSLeN4o874_mobile_small.jpg",
      						"middle":"http://fdfs.xmcdn.com/group3/M09/34/94/wKgDsVMUWC-i2BqxAALZkSLeN4o874_mobile_meduim.jpg",
      						"large":"http://fdfs.xmcdn.com/group3/M09/34/94/wKgDsVMUWC-i2BqxAALZkSLeN4o874_mobile_large.jpg",
						},
						"play_count":188300,
						"category_name":"资讯",
						"category_id":3,
						"update_time":"2017-03-03 10:09:18",  //更新时间
						"create_time":"2017-03-03 10:09:18",  //创建时间
						"source": "喜马拉雅",  //资源方
						"source_icon": "http://xxxx.xxx.xxx/xx/xx.jpg",  //资源方Icon
					}
				]
		}
}

```


### 2、获得某个专辑的节目列表
  * 接口地址：http://s.xiaodu.baidu.com/v20161223/unicast/tracklist
  * 请求方式：GET
  * 请求参数：

参数|类型|是否必须|备注
----|----|--------|----
albumid	|int	|是	|专辑ID
cuid	|string	|是	|设备ID，设备的唯一标识
appid   |string|是|appid,标识接入方
page	|int	|否	|页码，默认为1
pagesize	|int	|否	|每页数据量，默认为10
sort |int |否 |正序：acs、倒序：desc 

返回格式：
```javascript
{
	status: 0,
    code: "",
    data: 
        {
            "page" : 1,        //当前页
            "total_page" : 10,  //总页数
            "list" 
               [
					{
						"id":1,  //节目ID
						"track_title":"大保镖",  //节目名
						"duration":100,  //节目时长
						"cover_url": {							
						    "small":"http://fdfs.xmcdn.com/group3/M09/34/94/wKgDsVMUWC-i2BqxAALZkSLeN4o874_mobile_small.jpg",
      						"middle":"http://fdfs.xmcdn.com/group3/M09/34/94/wKgDsVMUWC-i2BqxAALZkSLeN4o874_mobile_meduim.jpg",
      						"large":"http://fdfs.xmcdn.com/group3/M09/34/94/wKgDsVMUWC-i2BqxAALZkSLeN4o874_mobile_large.jpg",
						},
						"play_count":188376,  //播放量
						"category_name":"相声",  //分类名
						"category_id":3,  //分类ID
						"update_time":1479966445, //更新时间
						"create_time":1481595445,  //创建时间
						"source": "喜马拉雅",  //资源方
						"source_icon": "XXX.icon",  //资源方Icon
					},
					{
						"id":1,
						"track_title":"逗你玩",
						"duration":160,
						"cover_url": {							
						    "small":"http://fdfs.xmcdn.com/group3/M09/34/94/wKgDsVMUWC-i2BqxAALZkSLeN4o874_mobile_small.jpg",
      						"middle":"http://fdfs.xmcdn.com/group3/M09/34/94/wKgDsVMUWC-i2BqxAALZkSLeN4o874_mobile_meduim.jpg",
      						"large":"http://fdfs.xmcdn.com/group3/M09/34/94/wKgDsVMUWC-i2BqxAALZkSLeN4o874_mobile_large.jpg",
						},
						"play_count":188300,
						"category_name":"资讯",
						"category_id":3,
						"update_time":"2017-03-03 10:09:18",  //更新时间
						"create_time":"2017-03-03 10:09:18",  //创建时间
						"source": "喜马拉雅",  //资源方
						"source_icon": "http://xxxx.xxx.xxx/xx/xx.jpg",  //资源方Icon
					}
				]
		}
}

```

### 3、获取节目信息
  * 接口地址：http://s.xiaodu.baidu.com/v20161223/unicast/trackplay
  * 请求方式：GET
  * 请求参数：

参数|类型|是否必须|备注
----|----|--------|----
trackid	|int	|是	|专辑ID
cuid	|string	|是	|设备ID，设备的唯一标识
appid   |string|是|appid,标识接入方
retry   |int|是|0是正常请求，大于0是失败后再次请求该节目资源

#### 播放url地址说明：
 * mp3\aac\m4a代表音频的格式
 * 32\64\128代表各个格式下32\64\128位的音频的播放地址
 * 注：每个音频会有多种格式多种码率的播放地址，但不是每种格式/码率的地址都有（端上要注意判断空），端上可根据支持的格式与网络情况按需取用相应的播放地址

返回格式：
```javascript
{
	status: 0,
	code: "",
	data:
		{
			"id":1,
			"track_title":"逗你玩",
			"duration":160,
			"cover_url":
			{								
			    "small":"http://fdfs.xmcdn.com/group3/M09/34/94/wKgDsVMUWC-i2BqxAALZkSLeN4o874_mobile_small.jpg",
      			"middle":"http://fdfs.xmcdn.com/group3/M09/34/94/wKgDsVMUWC-i2BqxAALZkSLeN4o874_mobile_meduim.jpg",
      			"large":"http://fdfs.xmcdn.com/group3/M09/34/94/wKgDsVMUWC-i2BqxAALZkSLeN4o874_mobile_large.jpg",
			},
			"play_count":188300,
			"category_name":"资讯",
			"category_id":3,
			"update_time":"2017-03-03 10:09:18",  //更新时间
			"create_time":"2017-03-03 10:09:18",  //创建时间
			"source": "喜马拉雅",  //资源方
			"source_icon": "http://xxxx.xxx.xxx/xx/xx.jpg",  //资源方Icon
			"play_url": 
			{
				"mp3":{//代表播放的音频格式
					"32": "http://fdfs.xmcdn.com/group3/M09/34/94/wKgDsVMUWC-i2BqxAALZkSLeN4o874_32.mp3",//代表32位mp3格式的声音的播放地址
					"64": "http://fdfs.xmcdn.com/group3/M09/34/94/wKgDsVMUWC-i2BqxAALZkSLeN4o874_64.mp3",//代表64位mp3格式的声音的播放地址
				},
				"acc":{					
					"32": "http://image.kaolafm.net/mz/aac_32/201305/1d257f2b-944d-4607-a846-15c8838a8aab.aac",
					"64": "http://image.kaolafm.net/mz/aac_64/201305/1d257f2b-944d-4607-a846-15c8838a8aab.aac",
					"128": "http://image.kaolafm.net/mz/aac_128/201305/1d257f2b-944d-4607-a846-15c8838a8aab.aac",
				},
				"m4a":{
						"24":"http://audio.xmcdn.com/group7/M03/03/FE/wKgDWlbB5mCj94OWAFBSGzSmA1g528.m4a",
					"64": "http://audio.xmcdn.com/group7/M03/03/DA/wKgDX1bB5l3S4rnMANJrwQTRSPo780.m4a",
				},
			},
		}
}

```


### 4、获取播放列表接口：
  * 接口地址：http://s.xiaodu.baidu.com/v20161223/unicast/playlist
  * 请求方式：GET
  * 请求参数：

参数|类型|是否必须|备注
----|----|--------|----
cuid	|string	|是	|设备ID，设备的唯一标识
appid|string|是|appid,标识接入方
page	|int	|否	|页码，默认为1
pagesize	|int	|否	|每页数据量，默认为10

返回格式：
```javascript
{
	status: 0,
	code: "",
	data:{
	    page : 1,
	    total_page : 10,
	    list:[
    		{
    			"id":1,
    			"track_title":"逗你玩",
    			"duration":160,
    			"cover_url": 
    			{								
    			    "small":"http://fdfs.xmcdn.com/group3/M09/34/94/wKgDsVMUWC-i2BqxAALZkSLeN4o874_mobile_small.jpg",
          			"middle":"http://fdfs.xmcdn.com/group3/M09/34/94/wKgDsVMUWC-i2BqxAALZkSLeN4o874_mobile_meduim.jpg",
          			"large":"http://fdfs.xmcdn.com/group3/M09/34/94/wKgDsVMUWC-i2BqxAALZkSLeN4o874_mobile_large.jpg",
    			},
    
    			"play_count":188300,
    			"category_name":"资讯",
    			"category_id":3,
    			"update_time":"2017-03-03 10:09:18",  //更新时间
    			"create_time":"2017-03-03 10:09:18",  //创建时间
    			"source": "喜马拉雅",  //资源方
    			"source_icon": "http://xxxx.xxx.xxx/xx/xx.jpg",  //资源方Icon
    		},
    		{
    			"id":2,
    			"track_title":"逗你玩",
    			"duration":160,
    			"cover_url": 
    			{								
    			    "small":"http://fdfs.xmcdn.com/group3/M09/34/94/wKgDsVMUWC-i2BqxAALZkSLeN4o874_mobile_small.jpg",
          			"middle":"http://fdfs.xmcdn.com/group3/M09/34/94/wKgDsVMUWC-i2BqxAALZkSLeN4o874_mobile_meduim.jpg",
          			"large":"http://fdfs.xmcdn.com/group3/M09/34/94/wKgDsVMUWC-i2BqxAALZkSLeN4o874_mobile_large.jpg",
    			},
    
    			"play_count":188300,
    			"category_name":"资讯",
    			"category_id":3,
    			"update_time":"2017-03-03 10:09:18",  //更新时间
    			"create_time":"2017-03-03 10:09:18",  //创建时间
    			"source": "喜马拉雅",  //资源方
    			"source_icon": "http://xxxx.xxx.xxx/xx/xx.jpg",  //资源方Icon
    		},
		]
	}
}

```

#### 5、播放历史接口：
 * 接口地址：http://s.xiaodu.baidu.com/v20161223/unicast/historylist
 * 请求方式：GET
 * 请求参数：

参数|类型|是否必须|备注
----|----|--------|----
cuid |string |是 |设备ID，设备的唯一标识 
appid|string|是|appid,标识接入方
page |int |否 |页码，默认为1
pagesize |int |否 |每页数据量，默认为10

 * 返回格式：
 
 ```javascript
 {
	status: 0,
	code: "",
	data:
		{
            "page" : 1,        //当前页
            "total_page" : 10,  //总页数
            "list" [
				{
					"id":1, //节目ID
					"track_title":"逗你玩",  //节目名
					"album_id":23,  //专辑ID
					"album_name": "逻辑思维",  //专辑名
					"duration": 220,  //节目时长，单位：s
					"offset": 100, //播放到的断点位置，单位：s，0为播放完毕
					"update_time":"2017-03-03 10:09:18",  //更新时间
					"create_time":"2017-03-03 10:09:18",  //创建时间
					"source": "喜马拉雅",  //资源方
					"source_icon": "http://xxxx.xxx.xxx/xx/xx.jpg",  //资源方Icon
				},
				{
					"id":2, //节目ID
					"track_title":"大保镖",  //节目名
					"album_id":23,  //专辑ID
					"album_name": "逻辑思维",  //专辑名
					"duration": 160,  //节目时长，单位：s
					"offset": 50, //播放到的断点位置，单位：s，0为播放完毕
					"update_time":"2017-03-03 10:09:18",  //更新时间
					"create_time":"2017-03-03 10:09:18",  //创建时间
					"source": "喜马拉雅",  //资源方
					"source_icon": "http://xxxx.xxx.xxx/xx/xx.jpg",  //资源方Icon
				},
			]
		}
}

 ```
6、按tag获取专辑列表信息
* 接口地址：http://s.xiaodu.baidu.com/v20161223/unicast/albumbytags
* 请求方式：GET
* 请求参数：

参数|类型|是否必须|备注
------|-----|-----|------
cuid|string|是|设备ID，设备的唯一标识
appid|string|是|唯一标识接入方
tags|string|是|需要查询的标签列表，多个标签用逗号(",")隔开 多个标签取结果的交集，比如标签"儿童,故事"，结果集是既包含儿童又包含故事的专辑列表
category| int |是|需要查询的标签所属的列表
page|int|否|页码，默认1
pagesize|int|否|每页数据量，默认10


分类ID|分类名称|标签列表
-------|--------|-------
1|相声 |郭德纲,岳云鹏
2|小说 |悬疑,玄幻,言情,都市
3|公开课|
4|诗歌| 抒情 
5|戏曲|豫剧 , 昆剧 , 京剧
6|段子|搞笑
7|讲座|互联网
8|演讲|科技
9|健康养生|饮食 , 运动
11|有声书|儿童 , 官场
12|资讯|国内 , 国外
13|历史|三国
14|评书|刘兰芳 , 单田芳
15|广播剧|电台广播
16|小品|赵本山
17|故事|儿童 , 情感
18|人文|名著
20|脱口秀娱乐

```
{
     status: 0,
     code: null,
     data:
        {
            "page" : 1,        //当前页
            "total_page" : 10,  //总页数
            "total_nums" : 1000,//分类下的专辑总量
            "list"
               [
                    {
                        "id":1,  //专辑ID
                        "album_title":"逻辑思维",  //专辑名
                        "include_track_count":100,  //节目总数
                        "cover_url": {
                            "small":"http://fdfs.xmcdn.com/group3/M09/34/94/wKgDsVMUWC-i2BqxAALZkSLeN4o874_mobile_small.jpg",
                                "middle":"http://fdfs.xmcdn.com/group3/M09/34/94/wKgDsVMUWC-i2BqxAALZkSLeN4o874_mobile_meduim.jpg",
                                "large":"http://fdfs.xmcdn.com/group3/M09/34/94/wKgDsVMUWC-i2BqxAALZkSLeN4o874_mobile_large.jpg",
                        },
                        "play_count":188376,  //播放量
                        "category_name":"资讯",  //分类
                        "category_id":3,  //分类ID
                        "update_time":1479966445,  //更新时间
                        "create_time":1481595445,  //创建时间
                        "source": "喜马拉雅",  //资源方
                        "source_icon": "XXX.icon",  //资源方Icon
                    },
                    {
                        "id":1,
                        "album_title":"逻辑思维2",
                        "include_track_count":160,
                        "cover_url": {                            "small":"http://fdfs.xmcdn.com/group3/M09/34/94/wKgDsVMUWC-i2BqxAALZkSLeN4o874_mobile_small.jpg",
                                "middle":"http://fdfs.xmcdn.com/group3/M09/34/94/wKgDsVMUWC-i2BqxAALZkSLeN4o874_mobile_meduim.jpg",
                                "large":"http://fdfs.xmcdn.com/group3/M09/34/94/wKgDsVMUWC-i2BqxAALZkSLeN4o874_mobile_large.jpg",
                        },
                        "play_count":188300,
                        "category_name":"资讯",
                        "category_id":3,
                        "update_time":1479966445,
                        "create_time":1481595445,
                    }
                ]
        }
}
```
7、一级类目信息查询
 
* 接口地址：http://s.xiaodu.baidu.com/v20161223/unicast/getcategory
* 请求方式：GET
* 请求参数：

参数|类型|是否必须|备注
-------|-----|----|-----
cuid|string|是|设备ID，设备的唯一标识
appid|string|是|唯一标识接入方

```
{
    status : 0,
    code: null,
    data: {
        list:[
            {
                categoryid : 1,
                categoryname : '相声',
                album_num : 300
            },
            {
                categoryid : 1,
                categoryname : '小品',
                album_num : 500
 
            }
        ]
    }
}
```
### 点播QU槽位

intent|slot|slot_name|slot_value
----|----|--------|----
intent::audio.unicast.play|点播播放	|一级分类	|first_category|小说、评书、相声等（{播放}+{点播泛词}的query的一级分类：default）
播放XXX与继续播放XXX无差别，都视为正常播放|搜索范围|search_list|favorite (收藏列表)，空为不限即全部	P1	 	新增，规则：当有播放收藏列表词时，出播放意图，此槽位=favorite
 	|主讲人|	artist	|郭德纲（演艺人员）|	P0	槽位已实现，后端检索已支持	词典完善，多值是否能实现待确认
 	|关键词	|keyword	|去除口语化后，意图/槽位 |不能识别的term，逗号分隔（qu做diff处理后的term）	P0	槽位已有，值未实现，后端检索已支持	实现未识别term填充
 	|二级分类	|second_category	|股市、儿童睡前故事	P1	槽位已实现	词典添加，后端检索支持
 	|节目名	|track_name	|大保镖	P0	槽位已实现	词典完善（与专辑名相同时，出节目名）
 	|专辑名	|album_name	| 	P0	槽位已实现	词典完善
 	|排序类型|	sort_type|	sort_new(最新) / sort_hot(最热)	P0	 	支持排序类语意解析
 	|来源	|source	|资源提供方 如：喜马拉雅	P1	 	新增，提供资源方名称词典
 	|标签	|tag	|其他属性词	P0	 	新增 ，提供属性词典
 	|第几集	|episode|	用于专辑内定位节目，值：整数，“最后一集”或“最新一集”时，值为：last	P0	 	新增， 示例：播放梅花三弄的第5集
 	|单位	|unit	|节目、专辑	P1	 	检索后端忽略此槽位
intent::audio.unicast.ask.track| 点播节目问答|	|
	|艺人|	artist	|艺人修饰槽位：非空有需求	P1	 	槽位格式修改，见前面的value说明
 	|专辑	|album	|专辑修饰槽位：非空有需求	P1	 	槽位格式修改，见前面的value说明
 	|第几集	|episode	|集修饰槽位：非空有需求，第五集，值为5	P1	 	槽位格式修改，见前面的value说明
 	|节目	|track	|节目修饰槽位：非空有需求	P1	 	槽位格式修改，见前面的value说明
intent::audio.unicast.ask.album |点播专辑问答||	
	|艺人	|artist|	艺人修饰槽位：非空有需求	
 	|节目	|track	|节目修饰槽位：非空有需求	P1	 	 
 	|集	|episode	|集修饰槽位：非空有需求，第五集，值为5		 
 	|专辑	|album	|专辑修饰槽位：非空有需求	P1	 	 
intent::audio.unicast.ask.artist |点播艺人问答	| 	| 	 	 	 	 
 	|节目	|track	|节目修饰槽位：非空有需求	P1	 	 
 	|专辑	|album	|专辑修饰槽位：非空有需求	P1	 	 
 	|集	|episode|集修饰槽位：非空有需求，第五集，值为5	 	 
 	|艺人	|artist	|艺人修饰槽位：非空有需求	P1	 	 
intent::audio.unicast.ask.episode|点播集问答||	
	|艺人	|artist	|艺人修饰槽位：非空有需求	P1	 	 
 	|节目	|track	|节目修饰槽位：非空有需求	P1	 	 
 	|专辑	|album	|专辑修饰槽位：非空有需求	P1	 	 
 	|集	|episode|集修饰槽位：默认为问第几集：1，第几集：1，剩多少集：2，总共多少集：3P1	  	 	 	 	 	 	 
intent::audio.unicast.favorite.album |点播专辑收藏	||
    |艺人	|artist	|艺人修饰槽位：非空有需求	P1	 	 
 	|节目	|track	|节目修饰槽位：非空有需求	P1	 	 
 	|专辑	|album	|专辑修饰槽位：非空有需求	P0	 	  	 	 	 	 	 	 
intent::audio.unicast.favorite.artist |点播艺人收藏||	
	|艺人	|artist	|艺人修饰槽位：非空有需求	P1	 	 
 	|节目	|track	|节目修饰槽位：非空有需求	P1	 	 
 	|专辑	|album	|专辑修饰槽位：非空有需求	P1	 	 
intent::audio.unicast.favorite.track点播节目收藏||	
	|艺人	|artist	|艺人修饰槽位：非空有需求	P1	 	 
 	|节目	|track	|节目修饰槽位：非空有需求	P1	 	 
 	|专辑	|album	|专辑修饰槽位：非空有需求	P1	 	  

#### 点播控制

intent	|slot	|slot_name	|slot_value|	指令动作|	指令说法
----|----|--------|------|--------|----
intent::audio.unicast.stop| 停止||||	 	 	 	 	 
intent::audio.unicast.pause |暂停||||	 	 	 	 	 
intent::audio.unicast.continue |继续||||	 	 	 	 	 
intent::audio.unicast.next |下一首	 	|||| 	 	 	 
intent::audio.unicast.previous |上一首	 	|||| 	 	 	 
intent::audio.unicast.nextalbum |下一专辑	 	|||| 	 	 	 
intent::audio.unicast.previousalbum |上一专辑	 	|||| 	 	 	 
intent::audio.unicast.play_mode| 播放模式	播放模式	|mode	|single_cycle，rand，list_cycle||
intent::audio.unicast.goto |跳转到指定节目集	| 	episode|	数字\last(最后一集)\new(最新一集)|	播放第几集、播放最后一集、播放最新一集
intent::audio.unicast.speed |快进/退	 |	|||
	|	|forward	|非空：快进需求，空：非快进|	 	 
 	| 	|forward_speed	|快进速度 ，int，倍数	| 	与端定默认速度
 	| 	|rewind	|非空：快退需求，空：非快退	 |	 
 	| 	|rewind_speed	|快退速度 ，int，倍数	| 	与端定默认速度
 	| 	|time	|单位：s	 	 