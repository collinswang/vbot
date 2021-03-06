
## 安装

### 环境要求

- PHP >= 7.0
- [PHP fileinfo 拓展](http://php.net/manual/en/book.fileinfo.php) 储存文件需要用到

### 安装

**请确保已经会使用composer！请确保已经会使用composer！请确保已经会使用composer！**

1、composer

```
composer require hanson/vbot
```

2、git

```
git clone https://github.com/HanSon/vbot.git
cd vbot
composer install
```

然后执行``` php example/index.php ``` 

PS:运行后二维码将保存于设置的缓存目录，命名为qr.png，控制台也会显示二维码，扫描即可（linux用户请确保已经打开ANSI COLOR）

*警告！执行前请先查看`index.php`的代码，注释掉你认为不需要的代码，避免对其他人好友造成困扰*

**请在terminal运行！请在terminal运行！请在terminal运行！**

## 体验

<img src="https://ws2.sinaimg.cn/large/685b97a1gy1fdordpa0cgj20e80e811z.jpg" height="320">

扫码后，验证输入“上山打老虎”即可自动加为好友并且拉入vbot群。

vbot并非24小时执行，有时会因为开发调试等原因暂停功能。如果碰巧遇到关闭情况，可加Q群 492548647 了解开放时间。执行后发送“拉我”即可自动邀请进群。

vbot示例源码为 https://github.com/HanSon/vbot/blob/master/example/index.php


## 文档

详细文档在[wiki](https://github.com/HanSon/vbot/wiki)中

### 小DEMO

[购书半自动处理](http://t.laravel-china.org/laravel-tutorial/5.1/buy-it)

[红包提醒](https://github.com/HanSon/vbot/blob/master/example/hongbao.php)

[轰炸消息到某群名](https://github.com/HanSon/vbot/blob/master/example/group.php)

[消息转发](https://github.com/HanSon/vbot/blob/master/example/forward.php)

[自定义处理器](https://github.com/HanSon/vbot/blob/master/example/custom.php)

[一键拜年](https://github.com/HanSon/vbot/blob/master/example/bainian.php)

[聊天操作](https://github.com/HanSon/vbot/blob/master/example/contact.php)


### 基本使用

```
// 图灵API自动回复
require_once __DIR__ . './../vendor/autoload.php';

use Hanson\Vbot\Foundation\Vbot;
use Hanson\Vbot\Message\Entity\Message;
use Hanson\Vbot\Message\Entity\Text;

$robot = new Vbot([
    'tmp' => '/path/to/tmp/', # 用于生成登录二维码以及文件保存
    'debug' => true # 用于是否输出用户组的json
]);

$robot->server->setMessageHandler(function($message){
    // 文字信息
    if ($message instanceof Text) {
        /** @var $message Text */
        // 联系人自动回复
        if ($message->fromType === 'Contact') {
            return 'hello vbot';
            // 群组@我回复
        } elseif ($message->fromType === 'Group' && $message->isAt) {
            return 'hello everyone';
        }
    }
});

$robot->server->run();

```

## to do list

vbot 已实现以及待实现的功能列表 [点击查看](https://github.com/HanSon/vbot/wiki/todolist)

## 参考项目

[lbbniu/WebWechat](https://github.com/lbbniu/WebWechat)

[littlecodersh/ItChat](https://github.com/littlecodersh/ItChat) 

感谢楼上两位作者曾对本人耐心解答

[liuwons/wxBot](https://github.com/liuwons/wxBot) 参考了整个微信的登录流程与消息处理

## 贡献者

排名不分先后，时间排序

[zhuanxuhit](https://github.com/zhuanxuhit) terminal显示二维码

[littlecodersh](https://github.com/littlecodersh) 分次加载好友数量方案

[yuanshi2016](https://github.com/yuanshi2016) 分次加载好友数量方案、登录域名方案以及测试

## Q&A

常见问题[点击查看](https://github.com/HanSon/vbot/wiki/Q&A)

有问题或者建议都可以提issue

或者加入vbot的QQ群：492548647

## donate 名单

vbot 的发展离不开大家的支持，无论是star或者donate，本人都衷心的感谢各位，也会尽自己的绵薄之力把 vbot 做到最好。

donate 名单 （排名按时间顺序）

|捐助者|金额|
|-----|----|
|[toby2016](https://github.com/toby2016)|￥5|
|A梦|￥18.88 * 4 |
|[summer](https://github.com/summerblue) 以及这是用vbot实现的半自动购书流程[Laravel 入门教程(推荐)](http://t.laravel-china.org/laravel-tutorial/5.1/buy-it)|￥66.66|
|匿名的某师兄| ￥181.8|

<img src="https://ww2.sinaimg.cn/large/685b97a1gy1fd61orxreaj20yf19fmz1.jpg" height="320"><img src="https://ww2.sinaimg.cn/large/685b97a1gy1fd61qscynwj20ng0zk0tx.jpg" height="320">
