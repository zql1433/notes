### 参考
* [PHP危险函数 - Exploitable PHP functions](https://stackoverflow.com/questions/3115559/exploitable-php-functions)
* [PHP安全编码 | WooYun知识库](http://su.xmd5.org/static/drops/tips-135.html#!)

### 准备
代码审计的前提:足够的开发能力

审计方法:
* 静态代码审计
* 动态调试跟踪

### 思路

* 搜索 危险函数 - 尝试利用

* 搜索 自定义安全过滤函数 - 尝试绕过
  * 常见的自定义函数名 `RemoveXSS`
  * 正则函数 `preg_replace`

* 搜索 输入输出点 - 紧跟来自用户的输入的逻辑走向 查看页面输出内容是否可控
  * 超全局变量 `$_GET $_POST $_SERVER $_SESSION $_COOKIE`等

### 实例1 PHP代码-系统命令执行漏洞

#### 设计

程序设计时就需要尽量避免使用命令执行函数。

#### 函数【执行系统命令的函数】

PHP中【执行系统命令的函数】，它们只有略微差别：
 ```
+----------------+-----------------+----------------+----------------+
|    Command     | Displays Output | Can Get Output | Gets Exit Code |
+----------------+-----------------+----------------+----------------+
| system()       | Yes (as text)   | Last line only | Yes            |
| passthru()     | Yes (raw)       | No             | Yes            |
| exec()         | No              | Yes (array)    | Yes            |
| shell_exec()   | No              | Yes (string)   | No             |
| backticks (``) | No              | Yes (string)   | No             |
+----------------+-----------------+----------------+----------------+
 ```

传入【执行系统命令的函数】的参数如果来自用户输入，必须进行严格的过滤/转义（如果此处没有正确实现，则可能存在命令注入）。

#### 修复方案

使用PHP自带的2个函数专门对命令字符串进行转义:escapeshellcmd和escapeshellarg
```
<?php
system(escapeshellcmd('pwd '.escapeshellarg("-L")));
//此时尝试进行命令注入：修改"-L"和'pwd '  会发现关键字符被转义 无法执行命令:
echo escapeshellcmd('pwd $#;` '.escapeshellarg("-L;id"));//输出为pwd \$\#\;\` '-L\;id'
?>
```

#### 修复原理

* escapeshellcmd  防止用户利用shell下的一些字符（如# ; `等）构造其他命令
* escapeshellarg  防止用户输入的内容逃逸出"参数值"的位置转而变成一个"参数选项"


escapeshellarg和escapeshellcmd 的C具体实现 331行
https://github.com/php/php-src/blob/321c0cc3493998f731f0666127c093eff4e119eb/ext/standard/exec.c

