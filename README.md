[如何将 Hugo 部署到 Netlify - 郝鸿涛::Hongtao Hao](https://hongtaoh.com/cn/2020/01/04/hugo-netlify-deploy/)

# 使用

1. 安装hugo 

2. 生成new site 

3. 下载主题，重命名 放到theme中，主题的expamlesite放到site目录下覆盖

4. 运行 theme=tokiow  draft 草稿形式。查看效果

5. 然后在site目录下 config.toml配置 参数，主题。

6. 删除public目录，上传github

   

---

### netlify配置

1. netlify添加新网站，选择仓库。

2. 域名，git gateway 。

#### 后台编辑配置

1. static 目录增加文件/admin 详见官方文档 。index.html config.yml文件。配置一些参数

2. 在项目根添加netlify.toml配置流程文件。环境变量hugo版本！
3. netlify查看日志 显示错误

#### 成员管理

公开注册或者私人

 

