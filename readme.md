# ESP8266 心知天气库  / ESP8266-Seniverse

*English description can be found at the end of Chinese description.*

## 基本介绍


此库用于ESP8266物联网开发板通过HTTP协议获取心知天气网站API所提供的免费信息。这些信息包括：

1. 天气预报信息（温度，天气，降水概率，风力，风向，湿度）
2. 实时天气信息（温度，天气）
3. 获取实时生活指数（穿衣，紫外线强度，洗车，旅游，感冒，运动）

关于以上信息的详细说明，请参考心知天气网站官方文档：https://www.seniverse.com/docs

心知天气成立于2016年，是中国领先的气象数据服务公司，致力于提供高精度的气象数据服务和产品。心知天气官网地址：www.seniverse.com 

## 关于本库

本库为太极创客团队制作的免费视频教程《零基础入门学用物联网 》中一部分。该教程系统的向您讲述ESP8266的物联网应用相关的软件和硬件知识。如果您希望观看教程视频，可前往以下视频平台观看。

哔哩哔哩：https://www.bilibili.com/video/BV1L7411c7jw

YouTube: https://www.youtube.com/playlist?list=PL8mx3Pk-gVLI2GwuxuqR_T5WDKeAPRkzj

ESP8266-Seniverse库仅仅是我们团队所开发的诸多免费开源项目中的一个。我们坚持免费开源是为了让更多的朋友可以体会开源项目和开源协作的魅力，让我们开发的项目更富活力。假如您喜欢我们的项目，请为本项目打上一颗小星星，或者把我们推荐给更多热爱科技的朋友们。谢谢！您的鼓励是我们前进最大的动力！

## 使用前准备工作

1. 使用本库前请预先注册好心知天气账号并且开通免费服务。
2. 本程序使用Arduino编程语言。如您使用Arduino IDE开发，请预先在Arduino IDE中安装好ESP8266扩展程序，如需了解详细安装方法，请参考太极创客团队制作的[《零基础入门学用物联网 - 基础知识篇》3-1-2 为ESP8266-NodeMCU搭建Arduino IDE开发环境](http://www.taichi-maker.com/homepage/esp8266-nodemcu-iot/iot-c/nodemcu-arduino-ide/)。
3. 本程序使用ArduinoJson库
   请预先在Arduino IDE中安装[ArduinoJson库](www.arduinojson.org)。 如果您想了解该库的具体使用方法，请参考太极创客团队制作的免费视频教程《[零基础入门学用物联网](http://www.taichi-maker.com/homepage/esp8266-nodemcu-iot/)》

## 使用方法

### 获取当前天气信息

1. 您可以参考example目录中的weather_now程序了解具体使用方法

2. 首先通过WeatherNow建立对象
   `WeatherNow weatherNow`

3. 使用config函数配置连接心知天气的用户私钥、城市信息以及温度
   `weatherNow.config(reqUserKey, reqLocation, reqUnit);`

4. 使用update函数对天气信息进行更新
   `weatherNow.update();`

5. 使用下列函数获取当前天气信息  
	
   | 函数说明                   | 函数示例                      |
   | -------------------------- | ----------------------------- |
   | 当前天气信息（字符串格式） | `weatherNow.getWeatherText()` |
   | 当前天气信息（整数格式）   | `weatherNow.getWeatherCode()` |
   | 当前温度信息               | `weatherNow.getDegree()`      |
   
6. 使用getServerCode函数可获取服务器响应状态码  `weatherNow.getServerCode()`

7. 使用getLastUpdate函数获取心知天气信息更新时间`weatherNow.getLastUpdate()`

### 获取天气预报信息

1. 您可以参考example目录中的forecast程序了解具体使用方法

2. 首先通过Forecast建立对象
   `Forecast forecast`

3. 使用config函数配置连接心知天气的用户私钥、城市信息以及温度
   `forecast.config(reqUserKey, reqLocation, reqUnit);`

4. 使用update函数对天气信息进行更新
   `forecast.update();`

5. 使用下列函数获取当前天气信息  

   | 函数说明                   | 函数示例（参数i为第几天信息）  |
   | -------------------------- | ------------------------------ |
   | 白天天气信息（字符串格式） | `forecast.getDayText(i)`       |
   | 白天天气信息（整数格式）   | `forecast.getDayCode(i)`       |
   | 夜晚天气信息（字符串格式） | `forecast.getNightText(i)`     |
   | 夜晚天气信息（整数格式）   | `forecast.getNightCode(i)`     |
   | 最高气温                   | `forecast.getHigh(i)`          |
   | 最低气温                   | `forecast.getLow(i)`           |
   | 心知天气信息更新时间       | `forecast.getLastUpdate(i)`    |
   | 获取降水概率信息           | `forecast.getRain(i)`          |
   | 获取风向信息               | `forecast.getWindDirection(i)` |
   | 获取风速信息               | `forecast.getWindSpeed(i)`     |
   | 获取风力信息               | `forecast.getWindScale(i)`     |
   | 获取湿度信息               | `forecast.getHumidity(i)`      |

6. 使用getServerCode函数可获取服务器响应状态码  `forecast.getServerCode()`

7. 使用getLastUpdate函数获取心知天气信息更新时间`forecast.getLastUpdate()`

### 获取生活指数信息

1. 您可以参考example目录中的life_info程序了解具体使用方法

2. 首先通过LIfeInfo建立对象
   `LifeInfo lifeInfo`

3. 使用config函数配置连接心知天气的用户私钥、城市信息以及温度
   `lifeInfo.config(reqUserKey, reqLocation, reqUnit);`

4. 使用update函数对天气信息进行更新
   `lifeInfo.update();`

5. 使用下列函数获取当前天气信息  

   | 函数说明       | 函数示例（参数i为第几天信息） |
   | -------------- | ----------------------------- |
   | 获取洗车建议   | `lifeInfo.getCarWash()`       |
   | 获取穿衣建议   | `lifeInfo.getDayCode()`       |
   | 获取流感建议   | `lifeInfo.getNightText(i)`    |
   | 获取运动建议   | `lifeInfo.getNightCode(i)`    |
   | 获取旅游建议   | `lifeInfo.getHigh(i)`         |
   | 获取紫外线建议 | `lifeInfo.getLow(i)`          |

6. 使用getServerCode函数可获取服务器响应状态码  `lifeInfo.getServerCode()`

7. 使用getLastUpdate函数获取心知天气信息更新时间`lifeInfo.getLastUpdate()`

太极创客团队信息
--------
太极创客官网地址：http://www.taichi-maker.com/

太极创客哔哩哔哩主页：https://space.bilibili.com/103589285

太极创客YouTube：https://www.youtube.com/channel/UC8EkxMr5gGnrb9adVgR-UJw

太极创客GitHub：https://github.com/taichi-maker

太极创客码云：https://gitee.com/taijichuangke

-----------------------------

## ESP8266-Seniverse

This ESP8266-Arduino Library is for getting weather information from Seniverse API (Free) via HTTP protocol. The information includes:

1. Weather Forecast（Temperature，Weather，Precipitation probability，Wind Scale，Wind Direction，Humidity）
2. Live Weather Info.（Temperature，Weather）
3. Daily Life Information（Dressing Suggestion，UV level etc.）

For more infromation about the above information please refer to Seniverse API Doc (Chinese Only)：https://www.seniverse.com/docs

founded in 2016, Seniverse is a leading Weather Data provider in China. Seniverse Official Website：www.seniverse.com 

About Taichi-Maker Team
--------

Taichi-Maker Official Website：http://www.taichi-maker.com/

Taichi-Maker BiliBili：https://space.bilibili.com/103589285

Taichi-Maker YouTube Chanel：https://www.youtube.com/channel/UC8EkxMr5gGnrb9adVgR-UJw

Taichi-Maker GitHub：https://github.com/taichi-maker

Taichi-Maker Gitee：https://gitee.com/taijichuangke



