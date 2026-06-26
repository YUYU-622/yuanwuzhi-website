# 腾讯云部署说明

这份说明面向第一版静态官网部署。当前项目是 Astro 静态站，构建后只需要把 `dist/` 上传到服务器即可。

## 一、本地构建

在项目目录执行：

```bash
npm install
npm run build
```

构建成功后，会生成：

```text
dist/
```

这个目录就是要部署到服务器的静态网站文件。

## 二、上传到腾讯云服务器

可以让技术同事通过 SFTP、宝塔面板、scp 或 Git 拉取方式上传。

建议服务器目录：

```text
/www/wwwroot/yuanwuzhi-website/
```

把 `dist/` 里的内容放进去，而不是把 `dist` 文件夹本身套进去。

正确结构示例：

```text
/www/wwwroot/yuanwuzhi-website/index.html
/www/wwwroot/yuanwuzhi-website/assets/
/www/wwwroot/yuanwuzhi-website/xiaokun/
/www/wwwroot/yuanwuzhi-website/yuanspace/
/www/wwwroot/yuanwuzhi-website/sitemap.xml
/www/wwwroot/yuanwuzhi-website/robots.txt
```

## 三、Nginx 配置示例

```nginx
server {
    listen 80;
    server_name yuanwuzhi.cn www.yuanwuzhi.cn;

    root /www/wwwroot/yuanwuzhi-website;
    index index.html;

    location / {
        try_files $uri $uri/ /index.html;
    }
}
```

配置后重载 Nginx：

```bash
nginx -t
systemctl reload nginx
```

## 四、域名与 HTTPS

1. 在域名 DNS 中，将 `yuanwuzhi.cn` 和 `www.yuanwuzhi.cn` 指向腾讯云服务器 IP。
2. 等解析生效后，申请 HTTPS 证书。
3. 配置 80 跳转 443。

## 五、上线前检查

- 首页、元小鲲、元Space 页面可访问。
- 图片正常加载。
- 移动端没有横向滚动。
- `https://www.yuanwuzhi.cn/sitemap.xml` 可访问。
- `https://www.yuanwuzhi.cn/robots.txt` 可访问。
- ICP 备案与公安备案信息按公司要求补到页脚。

## 六、暂不建议做的事

- 暂不接数据库。
- 暂不做后台 CMS。
- 暂不做复杂表单提交。
- 暂不把客户真实名称、价格、合同、具体配置写进官网。

第一版目标是先让官网主线、元小鲲、元Space 和 GEO 基础内容跑起来。
