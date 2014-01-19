# laravel-4.1-simple-blog

- 这是一个 laravel-4.1 的 Demo。
- 此项目采用模块化开发方式。

**注意：** 项目尚未编写结束。

---

- [模块化开发](#modules)
- [开发者信息保密方法](#assume-unchanged)

---

<a name="modules"></a>
### 模块化开发

#### 对于源程序的变动

**本质上没有修改任何源码。只是在使用方法上注意以下两点。**

\* `/app/config/view.php` 配置文件，增加模块公共视图目录。

    'paths' => array(
        __DIR__.'/../views',
        base_path('modules/views'), // 模块公共视图目录
    ),

\* `/app/routes.php` 路由文件中引用自定义的模块。（此为模块调用方法）

    /**
     * 模块化
     */
    include base_path('modules/functions.php');
    // 开发辅助
    module('5-say');
    // 权限
    module('Authority');
    // 管理员后台
    module('Admin');
    // 用户后台
    module('Account');
    // 博客
    module('Blog');

<a name="assume-unchanged"></a>
### 开发者信息保密方法

实际开发中（类似邮件功能）需要开发者私人密码的文件，可以采用以下方法进行隐私保护。**请在命令行中使用**。

    // 假设文件无改动，作用于版本库中已存在的文件。
    // 此方法将确保本地文件不提交，并且版本库中此文件的变更无法影响本地文件。
    git update-index --assume-unchanged app/config/mail.php
    // 取消并恢复为普通文件
    git update-index --no-assume-unchanged app/config/mail.php

