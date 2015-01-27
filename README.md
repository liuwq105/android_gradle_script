关于gralde的使用总结博客链接：[http://blog.csdn.net/colorapp/article/details/41779473](http://blog.csdn.net/colorapp/article/details/41779473)

### 使用方法：
1. 创建channel.txt，在其中输入渠道号名称以及渠道的数字，规则参考示例文件。需要说明一下的是，product flavor的是通过channel.txt动态生成的，通过读取channel.txt来动态生成flavor，可以根据需要自由改动。需要多少个渠道包，在channel.txt中输入多少行即可，注意最后一行不能为空。渠道较多的情况下，key可以不用填写，这是的key会默认使用渠道号加字母s做为渠道名称，参考脚本。
2. 在我们自己的应用中的渠道号需要两个参数，需要在manifest中添加两个${APP_KEY_PLACEHOLDER}和${APP_PID_PLACEHOLDER}，可以根据自己的项目需要修改manifest文件和不同的字段，参考示例manifest文件中的实现即可。打包脚本会在执行的时候会根据从channel.txt中读取的值动态替换这些字段。
3. 添加signing.properties文件，配置进行签名使用的参数，脚本会从这个文件中读取签名使用需要使用的参数，注意签名文件的路径需要设置绝对路径。
4. 添加proguard-rules.txt文件，添加自己的混淆规则。

=====================
### 题外话

2014年上半年开始接手Android开发，对Ant打包发布脚本实在是不习惯，并且我们的渠道包数量很大，每次打包都是一个痛苦的过程，后来折腾了两天写出来这个脚本，后续尽量随着AS一直进行更新。这个脚本还有些不够完善的地方，效率不够高，一次打包超过80个时会产生GC 问题，非常希望有人可以帮忙改进效率。也希望有人可以帮忙提供一些关于CI以及testing方面集成的建议。
