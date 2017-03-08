# 安装

- [安装](#安装)
    - [服务器要求](#服务器要求)
    - [安装 Django](#安装Django)
    - [配置](#配置)
- [Web 服务器配置](#Web服务器配置)
    - [美化 URLs](#美化URLs)

<a name="installation"></a>
## 安装


<a name="server-requirements"></a>
### 服务器要求

Django 框架对服务器有很少的要求，当然，很多的虚拟服务器已经满足这些要求，所以我们强烈推荐你使用[virtualenv](https://virtualenv.pypa.io/)和[virtualenvwrapper](https://virtualenvwrapper.readthedocs.io/en/latest/)作为你的本地开发环境。

不过，如果你没有使用 virtual 虚拟环境， 你需要你的服务器满足以下要求：

<div class="content-list" markdown="1">
- Python >= 2.7
- pip Extension
</div>

<a name="installing-django"></a>
### 安装Django

Django 使用[pip](https://pypi.python.org/pypi/pip) 来管理代码的依赖。所以，在使用 Django之前，请先确认你的电脑上安装了 pip。

#### 通过 pip 安装器

1.安装[pip](https://pip.pypa.io),最简单的是使用独立pip安装程序。如果您的发行版已经安装了pip，您可能需要更新它。
  如果它已过时，你会知道，因为安装将无法正常工作。
2.看看[virtualenv](https://virtualenv.pypa.io/)和[virtualenvwrapper](https://virtualenvwrapper.readthedocs.io/en/latest/)。这些工具提供了孤立的Python环境，这比在系统范围内安装包更实用。他们还允许安装没有管理员权限的软件包。
  参与的教程将介绍如何在Python 3上创建virtualenv。
3.创建并激活虚拟环境后，在shell提示符处输入`pip install Django`

#### 通过安装最新版的软件包

如果您使用Linux或Unix安装（如OpenSolaris），请与您的经销商联系，查看他们是否已经打包Django。如果你使用Linux发行版，不知道如何找到一个软件包是否可用，那么现在是学习的好时机。Django Wiki包含[第三方分发列表](https://code.djangoproject.com/wiki/Distributions)，以帮助您。

#### 本地开发环境

如果你在本地安装了Python,并且希望使用Python内置的开发环境服务器为应用提供服务，可以使用 `Django manage.py` 命令，这个命令会在本地环境启动开发环境服务器  `http://localhost:8000`:

    python manage.py runserver

当然，更强大的开发环境还是选择 [virtualenv](https://virtualenv.pypa.io/)和[virtualenvwrapper](https://virtualenvwrapper.readthedocs.io/en/latest/)

<a name="configuration"></a>
### 配置

#### 配置文件

Django 框架所有的配置都存放在`setting.py`文件里面，所有的配置都有注释，所以你可以轻松遍览这些配置文件以便熟悉所有配置项。 

#### 额外的配置

Django 几乎不需要其它任何配置就可以正常开发使用了。但是，建议你先浏览`setting.py`文件和对应的文档。其中包含了一些基于应用可能需要进行改变的配置，比如 time_zone 和 language_code（分别用于配置时区和本地化）。

你可能还想要配置 Django 的一些其它组件,例如：

<div class="content-list" markdown="1">
- [缓存](/docs/{{version}}/cache#configuration)
- [数据库](/docs/{{version}}/database#configuration)
- [Session](/docs/{{version}}/session#configuration)
</div>

<a name="web-server-configuration"></a>
## Web服务器配置

<a name="pretty-urls"></a>
### 美化URLs

#### Apache

Laravel includes a `public/.htaccess` file that is used to provide URLs without the `index.php` front controller in the path. Before serving Laravel with Apache, be sure to enable the `mod_rewrite` module so the `.htaccess` file will be honored by the server.

If the `.htaccess` file that ships with Laravel does not work with your Apache installation, try this alternative:

    Options +FollowSymLinks
    RewriteEngine On

    RewriteCond %{REQUEST_FILENAME} !-d
    RewriteCond %{REQUEST_FILENAME} !-f
    RewriteRule ^ index.php [L]

#### Nginx

If you are using Nginx, the following directive in your site configuration will direct all requests to the `index.php` front controller:

    location / {
        try_files $uri $uri/ /index.php?$query_string;
    }

Of course, when using [Homestead](/docs/{{version}}/homestead) or [Valet](/docs/{{version}}/valet), pretty URLs will be automatically configured.
