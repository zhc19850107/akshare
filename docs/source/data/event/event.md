## [AkShare](https://github.com/jindaxiang/akshare) 事件数据

### 新型冠状病毒-网易

接口: epidemic_163

目标地址: https://news.163.com/special/epidemic/

描述: 获取网易-新型冠状病毒-疫情数据

限量: 单次返回实时数据

输入参数

| 名称   | 类型 | 必选 | 描述                                                                              |
| -------- | ---- | ---- | --- |
| indicator | str | Y | indicator="实时", 返回实时数据; indicator="历史", 返回历史数据, 可能不及时 |

输出参数

| 名称          | 类型 | 默认显示 | 描述           |
| --------------- | ----- | -------- | ---------------- |
| country      | str   | Y        |   |
| area      | str   | Y        |   |
| city      | str   | Y        |   |
| confirm      | int   | Y        |   |
| suspect      | int   | Y        |   |
| dead      | int   | Y        |   |
| heal      | int   | Y        |   |
						
接口示例

```python
import akshare as ak
epidemic_163_df = ak.epidemic_163(indicator="实时")
print(epidemic_163_df)
```

数据示例-实时

```
    country area city  confirm  suspect  dead  heal
0        中国   湖北   武汉     1590        0    85    42
1        中国   湖北   黄冈      213        0     4     2
2        中国   湖北   孝感      173        0     1     0
3        中国   湖北   荆门      114        0     3     0
4        中国   湖北  恩施州       38        0     0     0
..      ...  ...  ...      ...      ...   ...   ...
316    斯里兰卡                  1        0     0     0
317      中国   吉林  公主岭        1        0     0     0
318      中国   海南   琼海        1        0     0     0
319      中国   海南  琼中县        1        0     0     0
320      中国   海南   东方        1        0     0     0
```

数据示例-历史

```
      day   time country  area  dead  confirm  suspect  heal  city district
0    1.12             中国  湖北武汉     1       41        0   NaN  None     None
1    1.13             中国  湖北武汉     1       41        0   NaN  None     None
2    1.14             中国  湖北武汉     1       41        0   NaN  None     None
3    1.15             中国  湖北武汉     2       41        0   NaN  None     None
4    1.16             中国  湖北武汉     2       45        0   NaN  None     None
..    ...    ...     ...   ...   ...      ...      ...   ...   ...      ...
220  1.26  09:00      中国    台湾     0        3        0   0.0               
221  1.26  09:00      中国    新疆     0        4        0   0.0               
222  1.26  09:00      中国    澳门     0        5        0   0.0               
223  1.26  09:00      中国   内蒙古     0        7        0   0.0               
224  1.26  09:00      中国    青海     0        4        0   0.0  
```

### 新型冠状病毒-丁香园

接口: epidemic_dxy

目标地址: http://3g.dxy.cn/newh5/view/pneumonia?scene=2&clicktime=1579615030&enterid=1579615030&from=groupmessage&isappinstalled=0

描述: 获取丁香园-新型冠状病毒-疫情数据

限量: 单次返回实时数据

输入参数-info

| 名称   | 类型 | 必选 | 描述                                                                              |
| -------- | ---- | ---- | --- |
| indicator | str | Y | indicator="info", 返回全国统计数据|

输出参数-info

| 名称          | 类型 | 默认显示 | 描述           |
| --------------- | ----- | -------- | ---------------- |
| 字符串      | str   | Y        |统计时间和情况概述   |

接口示例-info

```python
import akshare as ak
epidemic_dxy_df = ak.epidemic_dxy(indicator="info")
print(epidemic_dxy_df)
```

数据示例-info

```
                                                                0
abroadRemark                                                     
confirmedCount                                               6078
countRemark                                                      
createTime                                          1579537899000
curedCount                                                    115
dailyPic        https://img1.dxycdn.com/2020/0129/166/33936094...
deadCount                                                     132
deleted                                                     False
generalRemark                     疑似病例数来自国家卫健委数据，目前为全国数据，未分省市自治区等
id                                                              1
imgUrl          https://img1.dxycdn.com/2020/0123/733/33925757...
infectSource                                        野生动物，可能为中华菊头蝠
modifyTime                                          1580291081000
passWay                                         经呼吸道飞沫传播，亦可通过接触传播
remark1                 易感人群: 人群普遍易感。老年人及有基础疾病者感染后病情较重，儿童及婴幼儿也有发病
remark2                       潜伏期: 一般为 3~7 天，最长不超过 14 天，潜伏期内存在传染性
remark3                                                          
remark4                                                          
remark5                                                          
summary                                                          
suspectedCount                                               9239
virus                                            新型冠状病毒 2019-nCoV
```

输入参数-全国

| 名称   | 类型 | 必选 | 描述                                                                              |
| -------- | ---- | ---- | --- |
| indicator | str | Y | indicator="全国", 返回全国各省市统计数据|

输出参数-全国

| 名称          | 类型 | 默认显示 | 描述           |
| --------------- | ----- | -------- | ---------------- |
| 地区      | str   | Y        | 区域   |
| 地区简称      | str   | Y        | 区域   |
| 确诊      | str   | Y        | 数据  |
| 疑似      | str   | Y        | 数据  |
| 治愈      | str   | Y        | 数据  |
| 死亡      | str   | Y        | 数据  |
| 备注      | str   | Y        | 数据  |
					
接口示例-全国

```python
import akshare as ak
epidemic_dxy_df = ak.epidemic_dxy(indicator="全国")
print(epidemic_dxy_df)
```

数据示例-全国

```
          地区 地区简称   确诊  疑似  治愈  死亡             备注
0        湖北省   湖北  729   0  32  39               
1        广东省   广东   78   0   2   0               
2        浙江省   浙江   62   0   1   0               
3        重庆市   重庆   57   0   0   0               
4        湖南省   湖南   43   0   0   0               
5        北京市   北京   41   0   3   0               
6        安徽省   安徽   39   0   0   0               
7        上海市   上海   33   0   1   0               
8        河南省   河南   32   0   0   0               
9        四川省   四川   28   0   0   0               
10       山东省   山东   27   0   0   0               
11   广西壮族自治区   广西   23   0   0   0               
12       江西省   江西   18   0   0   0               
13       福建省   福建   18  20   0   0  福建地区新增疑似 20 例
14       江苏省   江苏   18   0   1   0               
15       海南省   海南   17   0   0   0               
16       辽宁省   辽宁   16   0   0   0               
17       陕西省   陕西   15   0   0   0               
18       云南省   云南   11   0   0   0               
19       天津市   天津   10   0   0   0               
20      黑龙江省  黑龙江    9   0   0   1               
21       河北省   河北    8   0   0   1               
22       山西省   山西    6   0   0   0               
23        香港   香港    5   0   0   0               
24       贵州省   贵州    4   0   0   0               
25       吉林省   吉林    4   0   0   0               
26       甘肃省   甘肃    4   0   0   0               
27   宁夏回族自治区   宁夏    3   0   0   0               
28        台湾   台湾    3   0   0   0               
29  新疆维吾尔自治区   新疆    3   0   0   0               
30        澳门   澳门    2   0   0   0               
31    内蒙古自治区  内蒙古    2   0   0   0               
32       青海省   青海    1   0   0   0               
```

输入参数-具体省份(如: 浙江省)

| 名称   | 类型 | 必选 | 描述                                                                              |
| -------- | ---- | ---- | --- |
| indicator | str | Y | indicator="浙江省", 返回具体省市统计数据|

输出参数-具体省份(如: 浙江省)

| 名称          | 类型 | 默认显示 | 描述           |
| --------------- | ----- | -------- | ---------------- |
| 区域      | str   | Y        | 区域   |
| 确诊人数      | str   | Y        | 数据  |
| 疑似人数      | str   | Y        | 数据  |
| 治愈人数      | str   | Y        | 数据  |
| 死亡人数      | str   | Y        | 数据  |
					
接口示例-具体省份(如: 浙江省)

```python
import akshare as ak
epidemic_dxy_df = ak.epidemic_dxy(indicator="浙江省")
print(epidemic_dxy_df)
```

数据示例-具体省份(如: 浙江省)

```
   区域  确诊人数  疑似人数  治愈人数  死亡人数
0  台州    20     0     0     0
1  杭州    12     0     0     0
2  温州    10     0     1     0
3  宁波     6     0     0     0
4  绍兴     4     0     0     0
5  嘉兴     4     0     0     0
6  舟山     2     0     0     0
7  金华     2     0     0     0
8  衢州     2     0     0     0           
```

输入参数-news

| 名称   | 类型 | 必选 | 描述                                                                              |
| -------- | ---- | ---- | --- |
| indicator | str | Y | indicator="news", 返回全国突发新闻数据|

输出参数-news

| 名称          | 类型 | 默认显示 | 描述           |
| --------------- | ----- | -------- | ---------------- |
| title      | str   | Y        |新闻标题   |
| summary      | str   | Y        | 数据概述  |
| infoSource      | str   | Y        | 新闻来源  |
| provinceName      | str   | Y        | 省份  |
| sourceUrl      | str   | Y        | 新闻地址  |

接口示例-news

```python
import akshare as ak
epidemic_dxy_df = ak.epidemic_dxy(indicator="news")
print(epidemic_dxy_df)
```

数据示例-news

```
                                          title  ...                                          sourceUrl
0                                    福建新增 1 例病例  ...      http://m.weibo.cn/2656274875/4464277568378388
1                                      上海启动一级响应  ...      http://m.weibo.cn/2803301701/4464275537960579
2                                      北京启动一级响应  ...      http://m.weibo.cn/2803301701/4464275537960579
3                               北京 1 新冠肺炎确诊患者出院  ...      http://m.weibo.cn/2803301701/4464259805726673
4                           国务院征集新冠肺炎疫情防控工作问题线索  ...  https://mp.weixin.qq.com/s/vQ-m0wW2cVZGYfJtAAMeiQ
5                                     天津确诊第 7 例  ...      http://m.weibo.cn/2656274875/4464245485576951
6                                      天津启动一级响应  ...      http://m.weibo.cn/2803301701/4464245166727843
7                                      安徽启动一级响应  ...      http://m.weibo.cn/2803301701/4464244898679663
8                            重磅！发热咳嗽非新冠肺炎唯一首发症状  ...    http://m.weibo.cn/2803301701/4464244348901450 ​
9                                  宁夏新增确诊1例疑似1例  ...      http://m.weibo.cn/2656274875/4464239232497670
10                     山东今日新增确诊 6 例，山东累计确诊 15 例  ...      http://m.weibo.cn/2803301701/4464230751473157
11                        福建新增确诊 4 例，福建累计确诊 9 例  ...      http://m.weibo.cn/2803301701/4464229795391738
12                                     武汉关闭过江隧道  ...      http://m.weibo.cn/2803301701/4464223541240916
13                                  内蒙古确诊首例新冠肺炎  ...    http://m.weibo.cn/2803301701/4464216926774457 ​
14                                     辽宁新增确诊1例  ...      http://m.weibo.cn/2803301701/4464215920401389
15                              转发提醒：这个春节尽量不聚会！  ...      http://m.weibo.cn/2803301701/4464209549089465
16                        海南新增确诊病例4例，海南累计确诊病例8例  ...     https://m.weibo.cn/2803301701/4464204335127376
17                      湖南新增确诊 15 例：湖南累计确诊 24 例  ...                             http://dxys.com/xyJAVU
18                    江苏新增新冠肺炎确诊病例4例，江苏累计新冠肺炎9例  ...        https://m.weibo.cn/status/4464192113565122?
19                      重庆新增确诊病例18例，重庆累计确诊病例27例  ...        https://m.weibo.cn/status/4464192578727481?
20        吉林新增2例新型肺炎确诊病例，吉林省累计报告新型冠状病毒感染的肺炎病例3例  ...        https://m.weibo.cn/status/4464191185997393?
21                   韩联社报道称，韩国出现第二例新型冠状病毒肺炎确诊病例  ...        https://m.weibo.cn/status/4464190838721454?
22                                 新疆新冠肺炎确诊病例2例  ...        https://m.weibo.cn/status/4464190448434604?
23                   四川新增新冠肺炎7例，四川累计新冠肺炎确诊病例15例  ...        https://m.weibo.cn/status/4464188997392969?
24                      浙江新增确诊病例16例，浙江累计确诊病例43例  ...  https://weibo.com/2803301701/IqVPiqaGC?ref=hom...
25           1月23日0时-24时，湖北省新增新型冠状病毒感染的肺炎病例105例  ...        https://m.weibo.cn/status/4464187650423052?
26                                 日本确诊2例新型肺炎病例  ...        https://m.weibo.cn/status/4464186283758930?
27  1月23日0-24时，黑龙江省报告新型冠状病毒感染的肺炎新增确诊病例2例，死亡病例1例  ...        https://m.weibo.cn/status/4464184127847534?
28        1月23日10时至24时，安徽省报告新型冠状病毒感染的肺炎新增确诊病例6例  ...        https://m.weibo.cn/status/4464183024267897?
29                               山东新增3例新型肺炎确诊病例  ...  https://weibo.com/2656274875/IqVDCt7bx?ref=hom...
30                              广东新冠肺炎新增确诊病例21例  ...  https://weibo.com/2803301701/IqVDxtTVg?ref=hom...
31                               河南新冠肺炎新增确诊病例4例  ...  https://weibo.com/2803301701/IqVxI77w5?ref=hom...
32                               全国确诊830例新型肺炎病例  ...  https://weibo.com/2656274875/IqVnfb1Hm?from=pa...
33                               上海新增4例新冠肺炎确诊病例  ...  https://weibo.com/2803301701/IqVhVnT9w?ref=hom...
34                                 武汉将以小汤山模式建医院  ...  https://weibo.com/2803301701/IqV7dq2sm?ref=hom...
35                         世卫组织：新型肺炎不构成国际突发卫生事件  ...  https://m.weibo.cn/status/4464150224652866?sud...
36                     北京新增4例新型肺炎确诊病例，累计确诊病例26例  ...        https://m.weibo.cn/status/4464099343625924?
37                               天津新增1例新型肺炎确诊病例  ...      http://m.weibo.cn/2656274875/4464091609170082
38                               广西新增新冠肺炎确诊病例8例  ...  https://www.weibo.com/2803301701/IqSJAANR5?fro...
39                           【湖北省新冠肺炎疫情防控指挥部通告】  ...  https://www.weibo.com/2803301701/IqSEcDHtL?fro...
40                           湖南启动重大突发公共卫生事件一级响应  ...  https://www.weibo.com/2803301701/IqSwMxPd0?fro...
41                         武汉开通24小时电话接收社会各界爱心捐赠  ...  https://mp.weixin.qq.com/s/cICSHZNVynQj7m63RSAv1Q
42                  文化和旅游部、国家文物局：出现疑似病人就地停止旅游活动  ...  https://mp.weixin.qq.com/s/cICSHZNVynQj7m63RSAv1Q
43                               河北 1 例新型肺炎病例死亡  ...  https://weibo.com/2656274875/IqSjFocrm?from=pa...
44                               江西新增 4 例新型肺炎病例  ...        https://m.weibo.cn/status/4464049040965675?
45                           湖北黄石 10 名疑似患者已隔离治疗  ...        https://m.weibo.cn/status/4464044838788193?
46                              昆明确诊第 2 例新型肺炎病例  ...        https://m.weibo.cn/status/4464047963266414?
47                              财政部拨10亿补助湖北防控疫情  ...      http://m.weibo.cn/2803301701/4464041822671982
```

输入参数-hospital

| 名称   | 类型 | 必选 | 描述                                                                              |
| -------- | ---- | ---- | --- |
| indicator | str | Y | indicator="hospital", 返回全国发热门诊数据|

输出参数-hospital

| 名称          | 类型 | 默认显示 | 描述           |
| --------------- | ----- | -------- | ---------------- |
| 省级行政区      | str   | Y        |-   |
| 市级      | str   | Y        | -  |
| 机构-医院      | str   | Y        | -  |

接口示例-hospital

```python
import akshare as ak
epidemic_dxy_df = ak.epidemic_dxy(indicator="hospital")
print(epidemic_dxy_df)
```

数据示例-hospital

```
   省级行政区  市级      机构／医院
0    湖北省  全省  定点医院/发热门诊
1    湖北省  武汉  定点医院/发热门诊
2    湖北省  荆门  定点医院/发热门诊
3    湖北省  宜昌  定点医院/发热门诊
4    湖北省  恩施  定点医院/发热门诊
..   ...  ..        ...
69    宁夏   /  定点医院/发热门诊
70    西藏   /  定点医院/发热门诊
71    新疆   /  定点医院/发热门诊
72    青海   /       定点医院
73    甘肃   /       定点医院
```

输入参数-plot

| 名称   | 类型 | 必选 | 描述                                                                              |
| -------- | ---- | ---- | --- |
| indicator | str | Y | indicator="plot", 绘制-全国疫情图 3 合 1|

输出参数-plot

| 名称          | 类型 | 默认显示 | 描述           |
| --------------- | ----- | -------- | ---------------- |
| 全国疫情新增趋势图      | str   | Y        |图片, 需要自己保存   |
| 全国疫情确诊/疑似累计趋势图      | str   | Y        |图片, 需要自己保存   |
| 全国疫情死亡/治愈累计趋势图      | str   | Y        |图片, 需要自己保存   |

接口示例-plot

```python
import akshare as ak
ak.epidemic_dxy(indicator="plot")
```

图片示例-plot

![](https://jfds-1252952517.cos.ap-chengdu.myqcloud.com/akshare/readme/event/epidemic_trend.jpg)

### 新型冠状病毒-百度

接口: epidemic_baidu

目标地址: https://voice.baidu.com/act/newpneumonia/newpneumonia/?from=osari_pc_1

描述: 获取百度-新型冠状病毒肺炎-疫情实时大数据报告

限量: 单次返回所有数据

输入参数-热门迁入地

| 名称   | 类型 | 必选 | 描述                                                                              |
| -------- | ---- | ---- | --- |
| indicator | str | Y | indicator="热门迁入地", 返回全国迁徙城市热门|

输出参数-热门迁入地

| 名称          | 类型 | 默认显示 | 描述           |
| --------------- | ----- | -------- | ---------------- |
| city_name      | str   | Y        |城市名称   |
| province_name      | str   | Y        |省份   |
| value      | str   | Y        |迁入比例   |
| city_code      | str   | Y        |各区县行政区划代码   |

接口示例-热门迁入地

```python
import akshare as ak
epidemic_baidu_df = ak.epidemic_baidu(indicator="热门迁入地")
print(epidemic_baidu_df)
```

数据示例-热门迁入地

```
   city_name province_name  value city_code
0        成都市           四川省   3.85    510100
1        北京市           北京市   3.32    110000
2        深圳市           广东省   3.09    440300
3        上海市           上海市   2.78    310000
4        广州市           广东省   2.72    440100
5        东莞市           广东省   2.17    441900
6        苏州市           江苏省   1.65    320500
7        重庆市           重庆市   1.65    500000
8        长沙市           湖南省   1.60    430100
9        昆明市           云南省   1.48    530100
10       沈阳市           辽宁省   1.41    210100
11       西安市           陕西省   1.40    610100
12       佛山市           广东省   1.33    440600
13       贵阳市           贵州省   1.32    520100
14       杭州市           浙江省   1.23    330100
15       郑州市           河南省   1.22    410100
16       南宁市       广西壮族自治区   1.22    450100
17       南京市           江苏省   1.20    320100
18       天津市           天津市   1.18    120000
19       合肥市           安徽省   1.09    340100
20       长春市           吉林省   1.07    220100
21      哈尔滨市          黑龙江省   0.98    230100
22       惠州市           广东省   0.97    441300
23       厦门市           福建省   0.96    350200
24       济南市           山东省   0.95    370100
25       青岛市           山东省   0.84    370200
26       中山市           广东省   0.83    442000
27       无锡市           江苏省   0.79    320200
28       太原市           山西省   0.75    140100
29       大连市           辽宁省   0.73    210200
```

输入参数-热门迁出地

| 名称   | 类型 | 必选 | 描述                                                                              |
| -------- | ---- | ---- | --- |
| indicator | str | Y | indicator="热门迁出地", 返回全国迁徙城市热门|

输出参数-热门迁出地

| 名称          | 类型 | 默认显示 | 描述           |
| --------------- | ----- | -------- | ---------------- |
| city_name      | str   | Y        |城市名称   |
| province_name      | str   | Y        |省份   |
| value      | str   | Y        |迁入比例   |
| city_code      | str   | Y        |各区县行政区划代码   |

接口示例-热门迁出地

```python
import akshare as ak
epidemic_baidu_df = ak.epidemic_baidu(indicator="热门迁出地")
print(epidemic_baidu_df)
```

数据示例-热门迁入地

```
   city_name province_name  value city_code
0        重庆市           重庆市   1.68    500000
1        成都市           四川省   1.27    510100
2        南充市           四川省   1.07    511300
3        广州市           广东省   0.98    440100
4        邵阳市           湖南省   0.88    430500
5        北京市           北京市   0.87    110000
6        盐城市           江苏省   0.87    320900
7        深圳市           广东省   0.82    440300
8        毕节市           贵州省   0.82    520500
9        达州市           四川省   0.81    511700
10       衡阳市           湖南省   0.73    430400
11       梅州市           广东省   0.72    441400
12       茂名市           广东省   0.72    440900
13       阜阳市           安徽省   0.71    341200
14       周口市           河南省   0.69    411600
15       长沙市           湖南省   0.66    430100
16       西安市           陕西省   0.66    610100
17       上海市           上海市   0.66    310000
18       曲靖市           云南省   0.66    530300
19       南宁市       广西壮族自治区   0.65    450100
20       湛江市           广东省   0.64    440800
21       玉林市       广西壮族自治区   0.61    450900
22       合肥市           安徽省   0.61    340100
23       资阳市           四川省   0.61    512000
24       揭阳市           广东省   0.61    445200
25       广安市           四川省   0.59    511600
26       内江市           四川省   0.59    511000
27       永州市           湖南省   0.59    431100
28       遵义市           贵州省   0.58    520300
29       绵阳市           四川省   0.58    510700
```

输入参数-今日疫情热搜

| 名称   | 类型 | 必选 | 描述                                                                              |
| -------- | ---- | ---- | --- |
| indicator | str | Y | indicator="今日疫情热搜", 返回今日疫情热搜数据|

输出参数-今日疫情热搜

| 名称          | 类型 | 默认显示 | 描述           |
| --------------- | ----- | -------- | ---------------- |
| degree      | str   | Y        | 搜索量   |
| query      | str   | Y        | 搜索内容  |
| type      | str   | Y        | 类型  |
| url      | str   | Y        | 网址  |
					
接口示例-今日疫情热搜

```python
import akshare as ak
epidemic_baidu_df = ak.epidemic_baidu(indicator="今日疫情热搜")
print(epidemic_baidu_df)
```

数据示例-今日疫情热搜

```
     degree            query type  \
0  25779382         新型肺炎实时动态    2   
1   2626725          疫情拐点将出现    1   
2   1935775   疫情被列国际突发公共卫生事件    2   
3   1337020    湖北企业复工不早于2.13    2   
4   1009220   病毒在毛质衣物上存活时间更短    0   
5    905491            火神山直播    0   
6    893315      包机接海外湖北公民回家    3   
7    779037  省委书记检查防疫被村口大爷拦住    3   
                                                 url  
0  https://m.baidu.com/s?word=%E6%96%B0%E5%9E%8B%...  
1  https://m.baidu.com/s?word=%E7%96%AB%E6%83%85%...  
2  https://m.baidu.com/s?word=%E7%96%AB%E6%83%85%...  
3  https://m.baidu.com/s?word=%E6%B9%96%E5%8C%97%...  
4  https://m.baidu.com/s?word=%E7%97%85%E6%AF%92%...  
5  https://m.baidu.com/s?word=%E7%81%AB%E7%A5%9E%...  
6  https://m.baidu.com/s?word=%E5%8C%85%E6%9C%BA%...  
7  https://m.baidu.com/s?word=%E7%9C%81%E5%A7%94%...         
```

输入参数-防疫知识热搜

| 名称   | 类型 | 必选 | 描述                                                                              |
| -------- | ---- | ---- | --- |
| indicator | str | Y | indicator="防疫知识热搜", 返回防疫知识热搜数据|

输出参数-防疫知识热搜

| 名称          | 类型 | 默认显示 | 描述           |
| --------------- | ----- | -------- | ---------------- |
| degree      | str   | Y        | 搜索量   |
| query      | str   | Y        | 搜索内容  |
| type      | str   | Y        | 类型  |
| url      | str   | Y        | 网址  |
					
接口示例-防疫知识热搜

```python
import akshare as ak
epidemic_baidu_df = ak.epidemic_baidu(indicator="防疫知识热搜")
print(epidemic_baidu_df)
```

数据示例-防疫知识热搜

```
    degree        query type  \
0  1802150     新型肺炎自查手册    0   
1   781468    新型冠状病毒的特征    0   
2   914125   n95口罩多久换一次    0   
3   801365    人的正常体温是多少    0   
4   599625  84消毒液对人体有害吗    3   
5   498645     钟南山示范摘口罩    3   
6   409385   戴口罩眼镜不起雾技巧    0   
7   109359    收快递会感染病毒吗    0   
                                                 url  
0  https://m.baidu.com/s?word=%E6%96%B0%E5%9E%8B%...  
1  https://m.baidu.com/s?word=%E6%96%B0%E5%9E%8B%...  
2  https://m.baidu.com/s?word=n95%E5%8F%A3%E7%BD%...  
3  https://m.baidu.com/s?word=%E4%BA%BA%E7%9A%84%...  
4  https://m.baidu.com/s?word=84%E6%B6%88%E6%AF%9...  
5  https://m.baidu.com/s?word=%E9%92%9F%E5%8D%97%...  
6  https://m.baidu.com/s?word=%E6%88%B4%E5%8F%A3%...  
7  https://m.baidu.com/s?word=%E6%94%B6%E5%BF%AB%...  
```

输入参数-热搜谣言粉碎

| 名称   | 类型 | 必选 | 描述                                                                              |
| -------- | ---- | ---- | --- |
| indicator | str | Y | indicator="热搜谣言粉碎", 返回热搜谣言粉碎数据|

输出参数-热搜谣言粉碎

| 名称          | 类型 | 默认显示 | 描述           |
| --------------- | ----- | -------- | ---------------- |
| degree      | str   | Y        | 搜索量   |
| query      | str   | Y        | 搜索内容  |
| type      | str   | Y        | 类型  |
| url      | str   | Y        | 网址  |
					
接口示例-热搜谣言粉碎

```python
import akshare as ak
epidemic_baidu_df = ak.epidemic_baidu(indicator="热搜谣言粉碎")
print(epidemic_baidu_df)
```

数据示例-热搜谣言粉碎

```
   degree         query type  \
0  219570    洗热水澡预防新型肺炎    7   
1   85560     纸币会传播冠状病毒    7   
2   68568     全身喷洒酒精可消毒    7   
3   39528   武汉红十字会收取服务费    7   
4   37296     风油精涂人中防流感    7   
5    7224    超市买的东西必须消毒    7   
6    4032      香油滴鼻孔防传染    7   
7    6696  世卫组织认定中国为疫区国    7   
                                                 url  
0  https://m.baidu.com/s?word=%E6%B4%97%E7%83%AD%...  
1  https://m.baidu.com/s?word=%E7%BA%B8%E5%B8%81%...  
2  https://m.baidu.com/s?word=%E5%85%A8%E8%BA%AB%...  
3  https://m.baidu.com/s?word=%E6%AD%A6%E6%B1%89%...  
4  https://m.baidu.com/s?word=%E9%A3%8E%E6%B2%B9%...  
5  https://m.baidu.com/s?word=%E8%B6%85%E5%B8%82%...  
6  https://m.baidu.com/s?word=%E9%A6%99%E6%B2%B9%...  
7  https://m.baidu.com/s?word=%E4%B8%96%E5%8D%AB%...  
```

输入参数-实时播报

| 名称   | 类型 | 必选 | 描述                                                                              |
| -------- | ---- | ---- | --- |
| indicator | str | Y | indicator="实时播报", 返回实时播报数据|

输出参数-实时播报

| 名称          | 类型 | 默认显示 | 描述           |
| --------------- | ----- | -------- | ---------------- |
| bjh_na      | str   | Y        |-   |
| eventDescription      | str   | Y        | 新闻描述  |
| eventTime      | str   | Y        | 新闻时间  |
| eventUrl      | str   | Y        | 链接  |
| homepageUrl      | str   | Y        | 链接  |
| item_avatar      | str   | Y        | -  |
| siteName      | str   | Y        | 新闻来源  |

接口示例-实时播报

```python
import akshare as ak
epidemic_baidu_df = ak.epidemic_baidu(indicator="实时播报")
print(epidemic_baidu_df)
```

数据示例-实时播报

```
                                               bjh_na  \
0   {'easyBrowse': '1', 'easyBrowseConfirm': '1', ...   
1                                                 NaN   
2   {'easyBrowse': '1', 'easyBrowseConfirm': '1', ...   
3   {'easyBrowse': '1', 'easyBrowseConfirm': '1', ...   
4   {'easyBrowse': '1', 'easyBrowseConfirm': '1', ...   
5   {'easyBrowse': '1', 'easyBrowseConfirm': '1', ...   
6                                                 NaN   
7   {'easyBrowse': '1', 'easyBrowseConfirm': '1', ...   
8   {'easyBrowse': '1', 'easyBrowseConfirm': '1', ...   
9   {'easyBrowse': '1', 'easyBrowseConfirm': '1', ...   
10                                                NaN   
11                                                NaN   
12                                                NaN   
13  {'easyBrowse': '1', 'easyBrowseConfirm': '1', ...   
14  {'easyBrowse': '1', 'easyBrowseConfirm': '1', ...   
15  {'easyBrowse': '1', 'easyBrowseConfirm': '1', ...   
16                                                NaN   
17  {'easyBrowse': '1', 'easyBrowseConfirm': '1', ...   
18  {'easyBrowse': '1', 'easyBrowseConfirm': '1', ...   
19  {'easyBrowse': '1', 'easyBrowseConfirm': '1', ...   
20  {'easyBrowse': '1', 'easyBrowseConfirm': '1', ...   
21  {'easyBrowse': '1', 'easyBrowseConfirm': '1', ...   
22                                                NaN   
23  {'easyBrowse': '1', 'easyBrowseConfirm': '1', ...   
24  {'easyBrowse': '1', 'easyBrowseConfirm': '1', ...   
25                                                NaN   
26  {'easyBrowse': '1', 'easyBrowseConfirm': '1', ...   
27  {'easyBrowse': '1', 'easyBrowseConfirm': '1', ...   
28  {'easyBrowse': '1', 'easyBrowseConfirm': '1', ...   
29                                                NaN   
30                                                NaN   
31  {'easyBrowse': '1', 'easyBrowseConfirm': '1', ...   
32                                                NaN   
33  {'easyBrowse': '1', 'easyBrowseConfirm': '1', ...   
34  {'easyBrowse': '1', 'easyBrowseConfirm': '1', ...   
35  {'easyBrowse': '1', 'easyBrowseConfirm': '1', ...   
                     eventDescription   eventTime  \
0            快讯！俄罗斯首次确诊两例新型冠状病毒感染肺炎病例  1580474901   
1           武汉市金银潭医院20名新型冠状病毒肺炎患者集体出院  1580474200   
2               财政部：确保居民不因担心费用问题而不敢就诊  1580473684   
3      湖北民政厅原副厅长文增显去世 是否感染新型冠状病毒肺炎未确诊  1580473063   
4         中央赴湖北指导组：进一步降低病死率 加强农村和社区防控  1580472650   
5          芬兰航空取消2月6日至2月29日期间中国内地全部航班  1580472257   
6      重磅！北京市政府：除必需行业外，各企业2月9日前灵活安排工作  1580472216   
7                         湖北将适当延长春节假期  1580469318   
8                长这样！雷神山医院隔离病区整体效果图发布  1580469098   
9              新加坡后天起禁止过去14天曾到中国的旅客入境  1580469076   
10       厦门实行口罩预约登记、摇号购买 登记系统今日14点已开放  1580468100   
11           准备起飞！祖国派专机接滞留马来西亚的武汉同胞回家  1580465635   
12                快讯！香港：从明日起 发烧旅客不准登机  1580465580   
13      感染孕产妇是否会对胎儿产生影响？马丁院士：现在还不能下结论  1580465303   
14            埃及航空暂停2月29日之前往返于中国大陆的航班  1580464878   
15        多家航司派出包机接湖北籍中国公民返乡，采取自愿购票原则  1580464838   
16           香港新型肺炎确诊病例增至12例，其中11例属输入  1580464114   
17       路透社：巴基斯坦暂停往返中国航班，2月2日后将再评估情况  1580463960   
18                   英国确诊2例新型冠状病毒感染肺炎  1580463912   
19         中疾控独家回应：“人传人”早有推论，保守下结论有原因  1580463633   
20           外地返京人员回不了家？北京市民政局：可向我们反映  1580462613   
21             商务部：前几天部分超市出现空架的情况明显缓解  1580461742   
22       林郑月娥：全港中小学、幼儿园以及特殊学校最快3月2日复课  1580461620   
23  北京卫健委发言人：有43例都是被家人感染，建议家人接触也要留有空间  1580461200   
24      北京市疾控中心副主任：对一般民众不太建议推广使用N95口罩  1580460671   
25         湖北红十字会对武汉、黄冈、孝感、荆门四市拨付款超1亿  1580460638   
26           广东31日0-12时新增确诊43例，新增出院1例  1580460300   
27         广东省卫健委：已做好在广深珠佛莞等市建临时医院的准备  1580459720   
28             湖北红会纠错莆田系医院口罩数量，结果又出错了  1580459430   
29         北京市卫健委发言人介绍9月大患者：为家庭密切接触感染  1580459407   
30       北京市民政局回应社区禁止外地人进入：非确诊病例应自由进入  1580458992   
31              北京新增7例新型肺炎确诊病例 累计139例  1580458448   
32       民政部回应家人被隔离后脑瘫儿死亡：加强特殊群体的关心帮扶  1580457600   
33         民政部回应社区劝阻租户入住：不宜一刀切，人心不能疏离  1580457246   
34                  卫健委：戴口罩跳广场舞还是有风险的  1580456929   
35           民政部：疫情解除前社区不能举办各类人员聚集性活动  1580456760   
                                             eventUrl  \
0   http://baijiahao.baidu.com/s?id=16572480255696...   
1   http://baijiahao.baidu.com/s?id=16572472690114...   
2   http://baijiahao.baidu.com/s?id=16572468473332...   
3   http://baijiahao.baidu.com/s?id=16572464180335...   
4   http://baijiahao.baidu.com/s?id=16572458307781...   
5   http://baijiahao.baidu.com/s?id=16572453392259...   
6   http://baijiahao.baidu.com/s?id=16572296217201...   
7   http://baijiahao.baidu.com/s?id=16572423157274...   
8   http://baijiahao.baidu.com/s?id=16572419102201...   
9   http://baijiahao.baidu.com/s?id=16572419989469...   
10  http://baijiahao.baidu.com/s?id=16572274167485...   
11  http://baijiahao.baidu.com/s?id=16572382862715...   
12  http://baijiahao.baidu.com/s?id=16572385604862...   
13  http://baijiahao.baidu.com/s?id=16572379462581...   
14  http://baijiahao.baidu.com/s?id=16572375985555...   
15  http://baijiahao.baidu.com/s?id=16572376024466...   
16  http://baijiahao.baidu.com/s?id=16572368444719...   
17  http://baijiahao.baidu.com/s?id=16572368038836...   
18  http://baijiahao.baidu.com/s?id=16572365082310...   
19  http://baijiahao.baidu.com/s?id=16572363429949...   
20  http://baijiahao.baidu.com/s?id=16572352076867...   
21  http://baijiahao.baidu.com/s?id=16572343604491...   
22  http://baijiahao.baidu.com/s?id=16572344014716...   
23  http://baijiahao.baidu.com/s?id=16572338358951...   
24  http://baijiahao.baidu.com/s?id=16572331048794...   
25  http://baijiahao.baidu.com/s?id=16572331928382...   
26  http://baijiahao.baidu.com/s?id=16572328951131...   
27  http://baijiahao.baidu.com/s?id=16572321483350...   
28  http://baijiahao.baidu.com/s?id=16572337126213...   
29  http://baijiahao.baidu.com/s?id=16572319400182...   
30  http://baijiahao.baidu.com/s?id=16572314353418...   
31  http://baijiahao.baidu.com/s?id=16572309679415...   
32  http://baijiahao.baidu.com/s?id=16572300663904...   
33  http://baijiahao.baidu.com/s?id=16572296788198...   
34  http://baijiahao.baidu.com/s?id=16572291786683...   
35  http://baijiahao.baidu.com/s?id=16572293117986...   
                                          homepageUrl  \
0   https://baijiahao.baidu.com/u?app_id=155196823...   
1   http://baijiahao.baidu.com/u?app_id=1551968238...   
2   https://baijiahao.baidu.com/u?app_id=156645361...   
3   https://baijiahao.baidu.com/u?app_id=156182596...   
4   https://baijiahao.baidu.com/u?app_id=155286491...   
5   https://baijiahao.baidu.com/u?app_id=156645361...   
6   http://baijiahao.baidu.com/u?app_id=1601149438...   
7   https://baijiahao.baidu.com/u?app_id=156645361...   
8   https://baijiahao.baidu.com/u?app_id=160114943...   
9   https://baijiahao.baidu.com/u?app_id=154660853...   
10  http://baijiahao.baidu.com/u?app_id=1561825967...   
11  http://baijiahao.baidu.com/u?app_id=1552864910...   
12  http://baijiahao.baidu.com/u?app_id=1549608413...   
13  https://baijiahao.baidu.com/u?app_id=156182596...   
14  https://baijiahao.baidu.com/u?app_id=156645361...   
15  https://baijiahao.baidu.com/u?app_id=157407200...   
16  http://baijiahao.baidu.com/u?app_id=1566453612...   
17  https://baijiahao.baidu.com/u?app_id=154960841...   
18  https://baijiahao.baidu.com/u?app_id=156182596...   
19  https://baijiahao.baidu.com/u?app_id=156645361...   
20  https://baijiahao.baidu.com/u?app_id=156645361...   
21  https://baijiahao.baidu.com/u?app_id=157316232...   
22  http://baijiahao.baidu.com/u?app_id=1549608413...   
23  https://baijiahao.baidu.com/u?app_id=154960841...   
24  https://baijiahao.baidu.com/u?app_id=156182596...   
25  http://baijiahao.baidu.com/u?app_id=1566453612...   
26  https://baijiahao.baidu.com/u?app_id=154960841...   
27  https://baijiahao.baidu.com/u?app_id=160198381...   
28  https://baijiahao.baidu.com/u?app_id=157224978...   
29  http://baijiahao.baidu.com/u?app_id=1566453612...   
30  http://baijiahao.baidu.com/u?app_id=1566453612...   
31  https://baijiahao.baidu.com/u?app_id=155286491...   
32  http://baijiahao.baidu.com/u?app_id=1549608413...   
33  https://baijiahao.baidu.com/u?app_id=156645361...   
34  https://baijiahao.baidu.com/u?app_id=160686343...   
35  https://baijiahao.baidu.com/u?app_id=154960841...   
                                          item_avatar siteName  
0   http://timg01.bdimg.com/timg?pacompress&imgtyp...     环球时报  
1   http://timg01.bdimg.com/timg?pacompress&imgtyp...     环球时报  
2   http://timg01.bdimg.com/timg?pacompress=&imgty...      新京报  
3   http://pic.rmb.bdstatic.com/d882b8d93b19c52206...     红星新闻  
4   http://timg01.bdimg.com/timg?pacompress=&imgty...  人民日报海外网  
5   http://timg01.bdimg.com/timg?pacompress=&imgty...      新京报  
6   http://pic.rmb.bdstatic.com/73c41abfdd401cc72e...  北京日报客户端  
7   http://timg01.bdimg.com/timg?pacompress=&imgty...      新京报  
8   http://pic.rmb.bdstatic.com/73c41abfdd401cc72e...  北京日报客户端  
9   http://timg01.bdimg.com/timg?pa=&imgtype=0&sec...     观察者网  
10  http://pic.rmb.bdstatic.com/d882b8d93b19c52206...     红星新闻  
11  http://timg01.bdimg.com/timg?pacompress=&imgty...  人民日报海外网  
12  http://timg01.bdimg.com/timg?pacompress=&imgty...      环球网  
13  http://pic.rmb.bdstatic.com/d882b8d93b19c52206...     红星新闻  
14  http://timg01.bdimg.com/timg?pacompress=&imgty...      新京报  
15  http://timg01.bdimg.com/timg?pacompress=&imgty...     澎湃新闻  
16  https://timg01.bdimg.com/timg?pacompress=&imgt...      新京报  
17  http://timg01.bdimg.com/timg?pacompress=&imgty...      环球网  
18  http://pic.rmb.bdstatic.com/d882b8d93b19c52206...     红星新闻  
19  http://timg01.bdimg.com/timg?pacompress=&imgty...      新京报  
20  http://timg01.bdimg.com/timg?pacompress=&imgty...      新京报  
21  http://timg01.bdimg.com/timg?pacompress=&imgty...      金融界  
22  http://timg01.bdimg.com/timg?pacompress=&imgty...      环球网  
23  http://timg01.bdimg.com/timg?pacompress=&imgty...      环球网  
24  http://pic.rmb.bdstatic.com/d882b8d93b19c52206...     红星新闻  
25  https://timg01.bdimg.com/timg?pacompress=&imgt...      新京报  
26  http://timg01.bdimg.com/timg?pacompress=&imgty...      环球网  
27  http://timg01.bdimg.com/timg?pacompress&imgtyp...   金十数据快讯  
28  http://timg01.bdimg.com/timg?pacompress=&imgty...     上游新闻  
29  https://timg01.bdimg.com/timg?pacompress=&imgt...      新京报  
30  https://timg01.bdimg.com/timg?pacompress=&imgt...      新京报  
31  http://timg01.bdimg.com/timg?pacompress=&imgty...  人民日报海外网  
32  http://timg01.bdimg.com/timg?pacompress=&imgty...      环球网  
33  http://timg01.bdimg.com/timg?pacompress=&imgty...      新京报  
34  http://pic.rmb.bdstatic.com/a51d142ac7625feda1...   潇湘晨报官方  
35  http://timg01.bdimg.com/timg?pacompress=&imgty...      环球网  
```

输入参数-历史

| 名称   | 类型 | 必选 | 描述                                                                              |
| -------- | ---- | ---- | --- |
| indicator | str | Y | indicator="历史", 返回全国疫情统计的历史数据|

输出参数-历史

| 名称          | 类型 | 默认显示 | 描述           |
| --------------- | ----- | -------- | ---------------- |
| 确诊      | str   | Y        |-   |
| 疑似      | str   | Y        | -  |
| 治愈      | str   | Y        | -  |
| 死亡      | str   | Y        | -  |

接口示例-历史

```python
import akshare as ak
epidemic_baidu_df = ak.epidemic_baidu(indicator="历史")
print(epidemic_baidu_df)
```

数据示例-历史

```
        确诊     疑似   治愈   死亡
1.21   440     37    0    0
1.22   574    393    0   17
1.23   835   1072   34   25
1.24  1297   1965   38   41
1.25  1985   2684   49   56
1.26  2761   5794   51   80
1.27  4535   6973   60  106
1.28  5997   9239  103  132
1.29  7736  12167  126  170
1.30  9720  15238  171  213
```

输入参数-国内

| 名称   | 类型 | 必选 | 描述                                                                              |
| -------- | ---- | ---- | --- |
| indicator | str | Y | indicator="国内", 国内疫情实时统计数据|

输出参数-国内

| 名称          | 类型 | 默认显示 | 描述           |
| --------------- | ----- | -------- | ---------------- |
| index      | str   | Y        |项目   |
|  value     | str   | Y        |数值(单位: 人)   |

接口示例-国内

```python
import akshare as ak
epidemic_baidu_df = ak.epidemic_baidu(indicator="国内")
print(epidemic_baidu_df)
```

数据示例-国内

```
            2020.01.31 20:52
confirmed               9811
died                     213
cured                    216
unconfirmed            15238
```

输入参数-国外

| 名称   | 类型 | 必选 | 描述                                                                              |
| -------- | ---- | ---- | --- |
| indicator | str | Y | indicator="国外", 国外疫情实时统计数据|

输出参数-国外

| 名称          | 类型 | 默认显示 | 描述           |
| --------------- | ----- | -------- | ---------------- |
| index      | str   | Y        |项目   |
| value     | str   | Y        |数值(单位: 人)   |

接口示例-国外

```python
import akshare as ak
epidemic_baidu_df = ak.epidemic_baidu(indicator="国外")
print(epidemic_baidu_df)
```

数据示例-国外

```
          2020.01.31 20:52
confirmed              122
died                     0
cured                   10
```

输入参数-具体省份(如: 浙江)

| 名称   | 类型 | 必选 | 描述                                                                              |
| -------- | ---- | ---- | --- |
| indicator | str | Y | indicator="浙江", 浙江疫情实时统计数据|

输出参数-具体省份(如: 浙江)

| 名称          | 类型 | 默认显示 | 描述           |
| --------------- | ----- | -------- | ---------------- |
| city      | str   | Y        |城市名称   |
| confirmed     | str   | Y        |确诊人数  |
| died     | str   | Y        |死亡人数   |
| crued     | str   | Y        |治愈人数   |

接口示例-具体省份(如: 浙江)

```python
import akshare as ak
epidemic_baidu_df = ak.epidemic_baidu(indicator="浙江")
print(epidemic_baidu_df)
```

数据示例-具体省份(如: 浙江)

```
   city confirmed died crued
0    台州        81          1
1    嘉兴        16           
2    湖州         6           
3    舟山         7          1
4    绍兴        23           
5    宁波        46           
6    杭州        85           
7    金华        27          2
8    丽水         7          1
9    温州       227          7
10   衢州        12           
```