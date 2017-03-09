# 目录结构

- [简介](#introduction)
- [创建你的应用程序](#create-your-app)
- [根目录](#the-root-directory)
    - [`站点` 文件夹](#the-root-site-directory)
    - [`app` 文件夹](#the-root-app-directory)
    - [`manage.py`文件](#the-manage-file)
- [站点目录](#the-site-directory)
- [App目录](#the-app-directory)

<a name="introduction"></a>
## 简介

Django 默认的目录结构意在为构建不同大小的应用提供一个好的起点，当然，你可以自己按照喜好组织应用目录结构。

<a name="create-your-app"></a>
## 创建你的应用程序

现在你的环境 - 一个“项目” - 已经设置，你将开始做工作。

您在Django中编写的每个应用程序都包含遵循特定约定的Python包。Django提供了一个自动生成应用程序的基本目录结构的实用程序，所以您可以专注于编写代码，而不是创建目录

> **项目与应用程序**

> 项目和应用程序之间有什么区别？应用程序是一个执行某些操作的Web应用程序 - 例如Weblog系统，公共记录数据库或简单的轮询应用程序。项目是特定网站的配置和应用程序的集合。项目可以包含多个应用程序。应用程序可以在多个项目中。

要创建您的应用程序，请确保您位于相同的目录中，manage.py 然后键入以下命令：

    python manage.py startapp app

这将创建一个目录app，其目录结构如下：

    app/ 
        migrations/
            __init__.py
        __init__.py 
        admin.py 
        models.py 
        tests.py
        views.py

Django 对类在何处被加载没有任何限制 -- 只要 站点目录的 `settings.py`的 `INSTALLED_APPS` 载入它们即可。

#### 页面模版目录在哪里?

许多初学者都会困惑 Laravel 为什么没有 models 目录,当然，这是 laravel 故意为之，因为 models 这个词对不同开发者而言有不同的含义，容易造成歧义，有些开发者认为应用的模型指的是业务逻辑，还有些开发者则认为模型指的是与关联数据库的交互。

正是因为如此，我们默认将 Eloquent 的模型放置到 app 目录下，从而允许开发者自行选择放置的位置。

<a name="the-root-directory"></a>
## 根目录

<a name="the-root-site-directory"></a>
### 站点文件夹

`站点` 目录，顾名思义，包含所有应用程序的配置文件。通读这些配置文件可以应对自己对配置修改的需求。

<a name="the-root-app-directory"></a>
### App文件夹

`app` 目录，如你所料，这里面包含应用程序的核心代码。另外，你为应用编写的代码绝大多数也会放到这里， 我们之后将很快对这个目录的细节进行深入探讨。

<a name="the-manage-file"></a>
### manage.py文件

`manage.py`是一个命令行实用程序，允许您以各种方式与此Django项目进行交互。您可以阅读[django-admin和manage.pymanage.py](https://docs.djangoproject.com/en/1.10/ref/django-admin/)中的所有详细信息。

<a name="the-site-directory"></a>
## 站点目录

`__init__.py` 文件是个空文件，告诉Python该目录应该被视为一个Python包。（如果你是Python初学者，请阅读官方Python文档中的[软件包](https://docs.python.org/tutorial/modules.html#packages)。）
`settings.py` 文件包含了此Django项目的设置/配置。 [Django设置](https://docs.djangoproject.com/en/1.8/topics/settings/)会告诉你所有关于设置如何工作.
`urls.py` 文件包含了Django项目的URL声明; 您的Django供电网站的“目录”。您可以在[网址调度程序](https://docs.djangoproject.com/en/1.8/topics/http/urls/)中详细了解网址。
`wsgl.py` 文件包含了与WSGI兼容的Web服务器为您的项目提供服务的入口点。有关更多详细信息，请参阅[如何使用WSGI](https://docs.djangoproject.com/en/1.8/howto/deployment/wsgi/)进行部署。

<a name="the-app-directory"></a>
## App目录

`migrations` 目录包含了数据迁移及填充文件，你还可以将其作为 SQLite 数据库的存放目录。
`__init__.py` 文件是个空文件，告诉Python该目录应该被视为一个Python包。
`admin.py` 文件用户设置Django 数据模型的管理后台应用程序配置文件。
`models.py` 文件包含了当前应用程序的模型类。
`tests.py` 文件包含了自动化测试。每一个测试类都需要添加 Test 前缀，你可以使用 `python manage.py test` 命令来运行测试。
`views.py` 文件包含了所有的控制器方法，用于处理HTTP请求的数据或者和`Templates`页面模版交互的。




