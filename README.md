# 豆瓣小组 API 分析

# 声明

以下所有 API 均由 __豆瓣（Douban.Inc）__ 提供，本人（Weidong Zheng）采取非正规手段获得。获取与共享之行为或有侵犯豆瓣权益的嫌疑。若被告知需停止共享与使用，本人会及时删除此页面与整个项目。

# API 说明

* 豆瓣小组的数据以 JSON 格式输出

* 网址中 `api` 后数字代表 API 版本，过高或过低均会返回错误信息

* 以下 API 在未特殊说明时，使用的 HTTP Method 均为 `GET`

* 以下 API 均需指定 `User-Agent` 字段。标记__需授权__的 API 必须有 `Authorization` 字段，其它则需要传 `apikey` 字段

# API 通用参数（可选）

* 以下参数均通用

| | 类型 | 说明 |
| ------------ | ------------- | ------------ |
| alt | 字符串  | 返回的数据格式，默认传 `json` |
| douban_udid | 字符串  | 根据设备udid计算出来 |
| event_loc_id | 整型 | 用户位置id，豆瓣内置的一套东西 |
| loc_id | 整型 | 与上方相同值 |
| latitude| 浮点型 | 用户坐标纬度 |
| longitude | 浮点型 | 用户坐标经度 |
| udid | 字符串 | 设备udid |
| version | 字符串 | APP 版本号 |

* 以下参数仅供列表类型 API 使用

| | 类型 | 说明 |
| ------------ | ------------- | ------------ |
| count | 整型  | 返回数据列表的数量 |
| start | 整型  | 指定数据列表的偏移 |

# API 分析

### 1. 查看用户所加入的小组

* URL: `https://frodo.douban.com/api/v2/group/user/:user_id/joined_groups`
* 输入用户的 `user_id` 拿到小组列表
* 响应实例:

```
{
    "count": 20,
    "start": 0,
    "total": 15,
    "groups": [
        {
            "domain": "P",
            "sharing_url": "https://www.douban.com/doubanapp/dispatch?uri=/group/146409",
            "member_count": 255294,
            "url": "https://www.douban.com/group/shanghaizufang/",
            "member_role": 1001,
            "desc_abstract": "一个背包，我们充满激情踏上了来上海的路。 \r\n\r\n☞每一个在外漂泊的人都会渴望有一个家，现在的家虽然是租来的，这也是一种生活，是人生的一个经历，当自己...",
            "join_type": "A",
            "uri": "douban://douban.com/group/146409",
            "unread_count": 244,
            "create_time": "2008-11-03 14:27:49",
            "avatar": "https://img1.doubanio.com/icon/g146409-8.jpg",
            "has_related_group_chats": true,
            "has_red_dot": false,
            "owner": {
                "kind": "user",
                "followed": false,
                "name": "River",
                "url": "https://www.douban.com/people/River.Holiu/statuses",
                "gender": "U",
                "reg_time": "2008-09-01 12:40:00",
                "uri": "douban://douban.com/user/2870956",
                "avatar": "https://img3.doubanio.com/icon/u2870956-2.jpg",
                "id": "2870956",
                "uid": "River.Holiu"
            },
            "type": "group",
            "id": "146409",
            "name": "上海租房"
        }, 
    ...
    ]
}
```

### 2. 查看我已发表的话题（需授权）

* URL: `https://frodo.douban.com/api/v2/group/user/posted_topics`
* 响应实例:

```
{
    "count": 30,
    "start": 0,
    "topics": [
        {
            "update_time": "2016-07-05 16:31:45",
            "group": {
                "domain": "P",
                "sharing_url": "https://www.douban.com/doubanapp/dispatch?uri=/group/196844",
                "member_count": 50232,
                "url": "https://www.douban.com/group/zufan/",
                "member_role": 1001,
                "desc_abstract": "在这里发布您租房和求租信息吧\r\n\r\n\r\n搬家后，也许你需要这些出口品：http://mianshe.tmall.com/\r\n\r\n\r\n商务合作请豆油。乱发广告一律删\r\n\r\n本站是给真正求租和...",
                "join_type": "A",
                "uri": "douban://douban.com/group/196844",
                "unread_count": 0,
                "create_time": "2009-12-03 15:11:47",
                "avatar": "https://img3.doubanio.com/icon/g196844-1.jpg",
                "has_related_group_chats": false,
                "owner": {
                    "kind": "user",
                    "followed": false,
                    "name": "菜菜OO",
                    "url": "https://www.douban.com/people/iamna/statuses",
                    "gender": "U",
                    "reg_time": "2009-01-20 15:53:56",
                    "uri": "douban://douban.com/user/3521698",
                    "avatar": "https://img3.doubanio.com/icon/u3521698-16.jpg",
                    "id": "3521698",
                    "uid": "iamna"
                },
                "type": "group",
                "id": "196844",
                "name": "上海租房@长宁租房/徐汇/静安租房"
            },
            "sharing_url": "https://www.douban.com/doubanapp/dispatch?uri=/group/topic/88130177",
            "title": "中山公园三泾南宅一室一厅求租！",
            "url": "https://www.douban.com/group/topic/88130177/",
            "author": {
                "kind": "user",
                "followed": false,
                "name": "消逝的年华",
                "url": "https://www.douban.com/people/75847671/statuses",
                "gender": "U",
                "reg_time": "2013-07-27 12:52:30",
                "uri": "douban://douban.com/user/75847671",
                "avatar": "https://img3.doubanio.com/icon/u75847671-3.jpg",
                "id": "75847671",
                "uid": "75847671"
            },
            "like_count": 2,
            "liked": false,
            "cover_url": "https://qnmob.doubanio.com/view/group_topic/large/public/p50687911.jpg?imageView2/2/q/90/w/120/h/90/format/webp",
            "uri": "douban://douban.com/group/topic/88130177",
            "is_locked": false,
            "create_time": "2016-07-04 17:17:19",
            "comments_count": 10,
            "type": "topic",
            "id": "88130177"
        },
    ...
    ]
}
```

### 3. 查看我所关注的小组最新话题（需授权）

* URL: `https://frodo.douban.com/api/v2/group/user/recent_topics`
* 响应实例:

```
{
    "has_more": true,
    "start": 0,
    "topics": [
        {
            "update_time": "2016-07-06 09:20:34",
            "group": {
                "domain": "P",
                "sharing_url": "https://www.douban.com/doubanapp/dispatch?uri=/group/146409",
                "member_count": 255307,
                "url": "https://www.douban.com/group/shanghaizufang/",
                "member_role": 1001,
                "desc_abstract": "一个背包，我们充满激情踏上了来上海的路。 \r\n\r\n☞每一个在外漂泊的人都会渴望有一个家，现在的家虽然是租来的，这也是一种生活，是人生的一个经历，当自己...",
                "join_type": "A",
                "uri": "douban://douban.com/group/146409",
                "unread_count": 0,
                "create_time": "2008-11-03 14:27:49",
                "avatar": "https://img1.doubanio.com/icon/g146409-8.jpg",
                "has_related_group_chats": true,
                "owner": {
                    "kind": "user",
                    "followed": false,
                    "name": "River",
                    "url": "https://www.douban.com/people/River.Holiu/statuses",
                    "gender": "U",
                    "reg_time": "2008-09-01 12:40:00",
                    "uri": "douban://douban.com/user/2870956",
                    "avatar": "https://img3.doubanio.com/icon/u2870956-2.jpg",
                    "id": "2870956",
                    "uid": "River.Holiu"
                },
                "type": "group",
                "id": "146409",
                "name": "上海租房"
            },
            "sharing_url": "https://www.douban.com/doubanapp/dispatch?uri=/group/topic/86339858",
            "title": "潍坊十村 精装一房 到世纪大道站只要10分钟 可乘2.4.6.9号线 看房联系18702115330 微信同号",
            "url": "https://www.douban.com/group/topic/86339858/",
            "author": {
                "kind": "user",
                "followed": false,
                "name": "小七",
                "url": "https://www.douban.com/people/145740311/statuses",
                "gender": "U",
                "reg_time": "2016-05-13 09:45:33",
                "uri": "douban://douban.com/user/145740311",
                "avatar": "https://img3.doubanio.com/icon/u145740311-2.jpg",
                "id": "145740311",
                "uid": "145740311"
            },
            "like_count": 4,
            "liked": false,
            "cover_url": "https://qnmob.doubanio.com/view/group_topic/large/public/p47142105.jpg?imageView2/2/q/90/w/120/h/90/format/webp",
            "uri": "douban://douban.com/group/topic/86339858",
            "is_locked": false,
            "create_time": "2016-05-13 09:58:16",
            "comments_count": 3667,
            "type": "topic",
            "id": "86339858"
        },
    ...
    ]
}
```

### 4. 查看话题详情

* URL: `https://frodo.douban.com/api/v2/group/topic/:topic_id`
* 输入 `topic_id` 拿到指定的话题详情
* 响应实例:

```
{
    "update_time": "2016-07-06 09:35:05",
    "locked": false,
    "sharing_url": "https://www.douban.com/doubanapp/dispatch?uri=/group/topic/88163163",
    "title": "顶级至尊↗-康定路-酒店式公寓",
    "url": "https://www.douban.com/group/topic/88163163/",
    "author": {
        "kind": "user",
        "followed": false,
        "name": "陶承鹏",
        "url": "https://www.douban.com/people/3801936/statuses",
        "gender": "U",
        "reg_time": "2009-03-13 16:06:49",
        "uri": "douban://douban.com/user/3801936",
        "avatar": "https://img3.doubanio.com/icon/u3801936-1.jpg",
        "id": "3801936",
        "uid": "3801936"
    },
    "like_count": 5,
    "uri": "douban://douban.com/group/topic/88163163",
    "cover_url": "https://qnmob.doubanio.com/view/group_topic/large/public/p50754069.jpg?imageView2/2/q/90/w/120/h/90/format/jpg",
    "content": "95区域：静安-曹家渡\r\n物业类型：酒店式公寓\r\n物业地址：康定路1033号\r\n户型：2室1厅1卫\r\n小区：同济佳苑\r\n面积：85平方米\r\n用途：住家办公(商用)均可\r\n所在楼层：3\r\n公交：23路、935路、148路、143路、45路、136路；同济佳苑\r\n附近地铁：地铁2、4、7、11号线。\r\n联系电话；18221286723\r\n微信号   ；410303308\r\n<图片1><图片2><图片3><图片4><图片5><图片6><图片7><图片8><图片9><图片10>",
    "photos": [
        {
            "layout": "C",
            "title": "",
            "seq_id": "1",
            "id": "50754069",
            "topic_id": "88163163",
            "alt": "https://qnmob.doubanio.com/view/group_topic/large/public/p50754069.jpg?imageView2/2/q/90/w/500/h/375/format/jpg",
            "creation_date": "2016-07-05 15:46:21",
            "author_id": "3801936",
            "size": {
                "width": 500,
                "height": 375
            }
        },
        ...
    ],
    "create_time": "2016-07-05 15:48:02",
    "comments_count": 1306,
    "group": {
        "domain": "P",
        "sharing_url": "https://www.douban.com/doubanapp/dispatch?uri=/group/146409",
        "member_count": 255311,
        "url": "https://www.douban.com/group/shanghaizufang/",
        "member_role": 1000,
        "desc_abstract": "一个背包，我们充满激情踏上了来上海的路。 \r\n\r\n☞每一个在外漂泊的人都会渴望有一个家，现在的家虽然是租来的，这也是一种生活，是人生的一个经历，当自己...",
        "join_type": "A",
        "uri": "douban://douban.com/group/146409",
        "unread_count": 0,
        "create_time": "2008-11-03 14:27:49",
        "avatar": "https://img1.doubanio.com/icon/g146409-8.jpg",
        "has_related_group_chats": true,
        "owner": {
            "kind": "user",
            "followed": false,
            "name": "River",
            "url": "https://www.douban.com/people/River.Holiu/statuses",
            "gender": "U",
            "reg_time": "2008-09-01 12:40:00",
            "uri": "douban://douban.com/user/2870956",
            "avatar": "https://img3.doubanio.com/icon/u2870956-2.jpg",
            "id": "2870956",
            "uid": "River.Holiu"
        },
        "type": "group",
        "id": "146409",
        "name": "上海租房"
    },
    "is_locked": false,
    "type": "topic",
    "id": "88163163"
}
```

### 5. 查看话题下的评论

* URL: `https://frodo.douban.com/api/v2/group/topic/:topic_id/comments`
* 输入 `topic_id` 拿到指定话题下的评论
* 响应实例:

```
{
    "popular_comments": [],
    "start": 0,
    "total": 14,
    "count": 20,
    "comments": [
        {
            "author": {
                "kind": "user",
                "followed": false,
                "name": "123456",
                "url": "https://www.douban.com/people/145926926/statuses",
                "gender": "U",
                "reg_time": "2016-05-17 17:47:05",
                "uri": "douban://douban.com/user/145926926",
                "avatar": "https://img1.doubanio.com/icon/user_normal.jpg",
                "id": "145926926",
                "uid": "145926926"
            },
            "text": "up",
            "vote_count": 0,
            "create_time": "2016-07-06 10:28:07",
            "voted": false,
            "id": "1150417424"
        },
    ...
    ]
}
```

### 6. 查看小组详情

* URL: `https://frodo.douban.com/api/v2/group/:group_id`
* 输入 `group_id` 拿到指定小组的详情
* 响应实例:

```
{
    "domain": "P",
    "latest_members": [
        {
            "kind": "user",
            "followed": false,
            "name": "✨ ωǒ ✨",
            "url": "https://www.douban.com/people/147959518/statuses",
            "gender": "F",
            "reg_time": "2016-07-06 10:08:48",
            "uri": "douban://douban.com/user/147959518",
            "avatar": "https://img3.doubanio.com/icon/u147959518-1.jpg",
            "id": "147959518",
            "uid": "147959518"
        },
    ...
    ],
    "member_role": 1000,
    "create_time": "2008-11-03 14:27:49",
    "owner": {
        "kind": "user",
        "followed": false,
        "name": "River",
        "url": "https://www.douban.com/people/River.Holiu/statuses",
        "gender": "U",
        "reg_time": "2008-09-01 12:40:00",
        "uri": "douban://douban.com/user/2870956",
        "avatar": "https://img3.doubanio.com/icon/u2870956-2.jpg",
        "id": "2870956",
        "uid": "River.Holiu"
    },
    "id": "146409",
    "background_image": "",
    "member_count": 255335,
    "desc_for_app": "",
    "name": "上海租房",
    "censor_message": "",
    "request_count": 0,
    "type": "group",
    "large_avatar": "https://img1.doubanio.com/view/group/medium/public/675f6a0efd8562b.jpg",
    "has_related_group_chats": true,
    "desc": "一个背包，我们充满激情踏上了来上海的路。 \r\n\r\n☞每一个在外漂泊的人都会渴望有一个家，现在的家虽然是租来的，这也是一种生活，是人生的一个经历，当自己在有家的日子里回想起来，这段别样的回忆或许也会留下点点甜蜜吧。\r\n☞合租房是共认的一种节省租金的一种租房方式，或者几个志趣相投的人同居在一起，或者同学或同事同租在一起。时代变迁，现在更有不同性别的男女同租一套房子，不光光省了租金，更留下了一段段值得回味的故事。 \r\n\r\n【备注】\r\n1、凡已经租出去的房子，标题前请注明  [已出租] ，可提高大家的找房效率！\r\n2、虽不反对公寓出租，但凡是如果 【发帖过多（超过四贴）或刷帖者】 一律永久封禁处理！\r\n\r\n【广而告之】\r\n点到健康，提供：上门按摩、推拿、足疗保健、小儿推拿、康复、SPA、催乳、艾灸、刮痧等。\r\nhttp://diandao.org/booking\r\n微信也可以下单，点到（微信号：diandaofuwu）",
    "sharing_url": "https://www.douban.com/doubanapp/dispatch?uri=/group/146409",
    "url": "https://www.douban.com/group/shanghaizufang/",
    "uri": "douban://douban.com/group/146409",
    "join_type": "A",
    "unread_count": 0,
    "avatar": "https://img1.doubanio.com/icon/g146409-8.jpg",
    "background_mask_color": "#309ece"
}
```

### 7. 查看小组下的所有话题

* URL: `https://frodo.douban.com/api/v2/group/:group_id/topics`
* 输入 `group_id` 拿到指定小组下的所有话题
* 响应实例:

```
{
    "count": 100,
    "start": 0,
    "topics": [
        {
            "update_time": "2016-07-06 10:48:22",
            "group": null,
            "sharing_url": "https://www.douban.com/doubanapp/dispatch?uri=/group/topic/88060613",
            "title": "1整租人民广场核心地段，知名小区长新大楼，现代温馨式装修，电梯房2室1厅，首次出租",
            "url": "https://www.douban.com/group/topic/88060613/",
            "author": {
                "kind": "user",
                "followed": false,
                "name": "A---郑加松",
                "url": "https://www.douban.com/people/146814559/statuses",
                "gender": "M",
                "reg_time": "2016-06-08 20:49:01",
                "uri": "douban://douban.com/user/146814559",
                "avatar": "https://img3.doubanio.com/icon/u146814559-4.jpg",
                "id": "146814559",
                "uid": "146814559"
            },
            "like_count": 9,
            "uri": "douban://douban.com/group/topic/88060613",
            "cover_url": "https://qnmob.doubanio.com/view/group_topic/large/public/p50541257.jpg?imageView2/2/q/90/w/120/h/90/format/webp",
            "is_locked": false,
            "create_time": "2016-07-02 15:41:08",
            "comments_count": 3012,
            "type": "topic",
            "id": "88060613"
        },
    ...
    ],
    "total": 238672
}
```

### 8. 查看小组的成员

* URL: `https://frodo.douban.com/api/v2/group/:group_id/members`
* 输入小组的 `group_id` 拿到该小组下的所有成员
* 响应实例:

```
{
    "count": 20,
    "admin_ids": [
        "2870956"
    ],
    "start": 0,
    "members": [
        {
            "kind": "user",
            "followed": false,
            "name": "River",
            "url": "https://www.douban.com/people/River.Holiu/statuses",
            "gender": "U",
            "reg_time": "2008-09-01 12:40:00",
            "uri": "douban://douban.com/user/2870956",
            "avatar": "https://img3.doubanio.com/icon/u2870956-2.jpg",
            "id": "2870956",
            "uid": "River.Holiu"
        },
    ...
    ],
    "total": 255348,
    "owner_id": "2870956"
}
```

### 9. 查看同类推荐的小组

* URL: `https://frodo.douban.com/api/v2/group/:group_id/related_groups`
* 输入小组的 `group_id` 拿到同种类型的小组列表
* 响应实例:

```
{
    "count": 8,
    "start": 0,
    "total": 8,
    "groups": [
        {
            "domain": "P",
            "latest_members": [
                {
                    "kind": "user",
                    "followed": false,
                    "name": "hahashike",
                    "url": "https://www.douban.com/people/147961571/statuses",
                    "gender": "M",
                    "reg_time": "2016-07-06 11:05:49",
                    "uri": "douban://douban.com/user/147961571",
                    "avatar": "https://img1.doubanio.com/icon/user_normal.jpg",
                    "id": "147961571",
                    "uid": "147961571"
                },
            ...
            ],
            "member_role": 1000,
            "create_time": "2007-12-25 19:52:38",
            "owner": {
                "kind": "user",
                "followed": false,
                "name": "强悍的兔子",
                "url": "https://www.douban.com/people/playwork/statuses",
                "gender": "M",
                "reg_time": "2007-04-27 16:03:02",
                "uri": "douban://douban.com/user/1529145",
                "avatar": "https://img1.doubanio.com/icon/u1529145-7.jpg",
                "id": "1529145",
                "uid": "playwork"
            },
            "id": "76231",
            "background_image": "https://img1.doubanio.com/view/group/large/public/af5aecc90c0bf77.jpg",
            "member_count": 88735,
            "desc_for_app": "",
            "name": "上海租房---房子是租来的，生活不是",
            "censor_message": "",
            "type": "group",
            "large_avatar": "https://img1.doubanio.com/view/group/medium/public/397a153585ec19c.jpg",
            "has_related_group_chats": false,
            "desc": "小组口号： 我们都在这个城市流浪，寻找的不是那张床，是梦想。\r\n\r\n为什么在这个小组找房子：\r\n\r\n>本小组有小组长心细打理，力图使小组信息分享流畅简洁，帮您所急；\r\n>定期清理搬家，二手货物，群租房等小广告\r\n>优质信息置顶推荐，您也可以豆油我要求置顶您的紧急信息，记得附上链接\r\n>本小组已经帮助上千豆友找到了理想的合租伙伴，我们会继续下去\r\n>支持小组，请点击置顶广告，如果我帮你置顶了，请点击广告回馈\r\n",
            "sharing_url": "https://www.douban.com/doubanapp/dispatch?uri=/group/76231",
            "url": "https://www.douban.com/group/homeatshanghai/",
            "uri": "douban://douban.com/group/76231",
            "join_type": "A",
            "unread_count": 0,
            "avatar": "https://img3.doubanio.com/icon/g76231-3.jpg",
            "background_mask_color": "#9933bc86"
        },
    ...
    ]
}
```

### 10. 搜索小组下的话题

* URL: `https://frodo.douban.com/api/v2/group/:group_id/search/topic`
* 附加参数: `q=[string]` | __关键词__
* 输入小组的 `group_id` 和关键词拿到搜索的列表
* 响应实例:

```
{
    "count": 20,
    "start": 0,
    "topics": [
        {
            "update_time": "2013-10-24 11:31:21",
            "group": {
                "domain": "P",
                "sharing_url": "https://www.douban.com/doubanapp/dispatch?uri=/group/146409",
                "member_count": 255355,
                "url": "https://www.douban.com/group/shanghaizufang/",
                "member_role": 1000,
                "desc_abstract": "一个背包，我们充满激情踏上了来上海的路。 \r\n\r\n☞每一个在外漂泊的人都会渴望有一个家，现在的家虽然是租来的，这也是一种生活，是人生的一个经历，当自己...",
                "join_type": "A",
                "uri": "douban://douban.com/group/146409",
                "unread_count": 0,
                "create_time": "2008-11-03 14:27:49",
                "avatar": "https://img1.doubanio.com/icon/g146409-8.jpg",
                "has_related_group_chats": true,
                "owner": {
                    "kind": "user",
                    "followed": false,
                    "name": "River",
                    "url": "https://www.douban.com/people/River.Holiu/statuses",
                    "gender": "U",
                    "reg_time": "2008-09-01 12:40:00",
                    "uri": "douban://douban.com/user/2870956",
                    "avatar": "https://img3.doubanio.com/icon/u2870956-2.jpg",
                    "id": "2870956",
                    "uid": "River.Holiu"
                },
                "type": "group",
                "id": "146409",
                "name": "上海租房"
            },
            "sharing_url": "https://www.douban.com/doubanapp/dispatch?uri=/group/topic/45152305",
            "title": "我愿意承担你一半的房租，只要我回上海的时候你收留我",
            "url": "https://www.douban.com/group/topic/45152305/",
            "author": {
                "kind": "user",
                "followed": false,
                "name": "IT大神",
                "url": "https://www.douban.com/people/3679705/statuses",
                "gender": "F",
                "reg_time": "2009-02-21 13:36:32",
                "uri": "douban://douban.com/user/3679705",
                "avatar": "https://img3.doubanio.com/icon/u3679705-10.jpg",
                "id": "3679705",
                "uid": "3679705"
            },
            "like_count": 1,
            "uri": "douban://douban.com/group/topic/45152305",
            "cover_url": "",
            "is_locked": false,
            "create_time": "2013-10-23 16:06:27",
            "comments_count": 31,
            "type": "topic",
            "id": "45152305"
        },
    ...
    ],
    "total": 26593
}
```

### 11. 全局搜索小组

* URL: `https://frodo.douban.com/api/v2/group/search/group`
* 附加参数: `q=[string]` | __关键词__
* 输入关键词即可搜索小组
* 响应实例:

```
{
    "count": 5,
    "start": 0,
    "total": 9800,
    "groups": [
        {
            "domain": "P",
            "sharing_url": "https://www.douban.com/doubanapp/dispatch?uri=/group/39251",
            "member_count": 552641,
            "url": "https://www.douban.com/group/lvxing/",
            "member_role": 1000,
            "desc_abstract": "我们爱旅行，我们爱摄影，因为我们爱生活……\r\n\r\n注意：户外俱乐部广告、频繁自顶贴内容、借贴游记或者摄影内容加网址推广网站帖一律删除，酌情封禁，不单独...",
            "join_type": "A",
            "uri": "douban://douban.com/group/39251",
            "unread_count": 0,
            "create_time": "2007-03-13 16:32:27",
            "avatar": "https://img3.doubanio.com/icon/g39251-1.jpg",
            "has_related_group_chats": true,
            "owner": {
                "kind": "user",
                "followed": false,
                "name": "小涛",
                "url": "https://www.douban.com/people/happyelf/statuses",
                "gender": "M",
                "reg_time": "2005-08-29 18:04:23",
                "uri": "douban://douban.com/user/1017473",
                "avatar": "https://img3.doubanio.com/icon/u1017473-24.jpg",
                "id": "1017473",
                "uid": "happyelf"
            },
            "type": "group",
            "id": "39251",
            "name": "爱旅行爱摄影"
        },
    ...
    ]
}
```

### 12. 全局搜索话题

* URL: `https://frodo.douban.com/api/v2/group/search/topic`
* 附加参数: `q=[string]` | __关键词__
* 输入关键词即可搜索到话题
* 响应实例:

```
{
    "count": 5,
    "start": 0,
    "topics": [
        {
            "update_time": "2015-01-28 14:50:30",
            "group": {
                "domain": "P",
                "sharing_url": "https://www.douban.com/doubanapp/dispatch?uri=/group/222497",
                "member_count": 175,
                "url": "https://www.douban.com/group/222497/",
                "member_role": 1000,
                "desc_abstract": "差点忘了，大家都是小组长",
                "join_type": "A",
                "uri": "douban://douban.com/group/222497",
                "unread_count": 0,
                "create_time": "2010-02-28 19:05:24",
                "avatar": "https://img3.doubanio.com/icon/g222497-2.jpg",
                "has_related_group_chats": false,
                "owner": {
                    "kind": "user",
                    "followed": false,
                    "name": "没有切菜的刀",
                    "url": "https://www.douban.com/people/4247997/statuses",
                    "gender": "U",
                    "reg_time": "2009-05-23 02:28:18",
                    "uri": "douban://douban.com/user/4247997",
                    "avatar": "https://img3.doubanio.com/icon/u4247997-6.jpg",
                    "id": "4247997",
                    "uid": "4247997"
                },
                "type": "group",
                "id": "222497",
                "name": "虎门摄影"
            },
            "sharing_url": "https://www.douban.com/doubanapp/dispatch?uri=/group/topic/32547308",
            "title": "虎门摄影 虎门淘宝摄影 常平摄影 常平淘宝摄影 塘厦摄影 塘厦淘宝摄影 黄江摄影 黄江淘宝摄影 谢岗摄影 谢岗淘宝摄影 樟木头摄影 樟木头淘宝摄影 大岭山摄影 大岭山淘宝摄影 沙田摄影 沙田淘宝摄影",
            "url": "https://www.douban.com/group/topic/32547308/",
            "author": {
                "kind": "user",
                "followed": false,
                "name": "明王子",
                "url": "https://www.douban.com/people/64411879/statuses",
                "gender": "U",
                "reg_time": "2012-09-04 10:34:49",
                "uri": "douban://douban.com/user/64411879",
                "avatar": "https://img1.doubanio.com/icon/user_normal.jpg",
                "id": "64411879",
                "uid": "64411879"
            },
            "like_count": 16,
            "uri": "douban://douban.com/group/topic/32547308",
            "cover_url": "",
            "is_locked": false,
            "create_time": "2012-09-06 11:07:51",
            "comments_count": 1,
            "type": "topic",
            "id": "32547308"
        },
    ...
    ],
    "total": 504557
}
```

### 13. 发表新评论（需授权）

* URL: `https://frodo.douban.com/api/v2/group/topic/:topic_id/add_comment`
* 附加参数: `content=[string]` | __评论的内容__
* 输入话题的 `topic_id` 和评论内容即可
* 响应实例:

```
{
    "author": {
        "kind": "user",
        "followed": false,
        "name": "消逝的年华",
        "url": "https://www.douban.com/people/75847671/statuses",
        "gender": "U",
        "reg_time": "2013-07-27 12:52:30",
        "uri": "douban://douban.com/user/75847671",
        "avatar": "https://img3.doubanio.com/icon/u75847671-3.jpg",
        "id": "75847671",
        "uid": "75847671"
    },
    "text": "我顶",
    "vote_count": 0,
    "create_time": "2016-07-14 13:40:12",
    "voted": false,
    "id": "1156599879"
}
```
