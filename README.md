# 元物质官网新版

这是元物质官网重构与 GEO 内容优化项目。第一版目标是先跑通一个可预览、可构建、可部署的静态官网，用于承接元小鲲科研智算一体机、元Space 和元物质“科研智算能力建设伙伴”的新叙事。

## 当前页面

- `/` 首页
- `/scenarios/` 科研场景
- `/products/` 产品与能力
- `/xiaokun/` 元小鲲科研智算一体机
- `/yuanspace/` 元Space 科研智算平台
- `/cases/` 客户实践
- `/research-computing/` 科研智算
- `/resources/` 动态与资源
- `/support/` 技术支持
- `/about/` 关于元物质
- `/contact/` 联系我们
- `/faq/` FAQ

## 技术栈

- Astro 静态站
- 纯静态输出
- 适合部署到腾讯云服务器 + Nginx，也可以后续接入腾讯云静态网站托管

## 本地运行

```bash
npm install
npm run dev
```

默认本地地址：

```text
http://127.0.0.1:4321/
```

## 构建

```bash
npm run build
```

构建产物在 `dist/`。

## 预览构建产物

```bash
npm run preview
```

## 部署到腾讯云服务器的基本方式

1. 在本地执行：

   ```bash
   npm install
   npm run build
   ```

2. 将 `dist/` 目录上传到腾讯云服务器，例如：

   ```text
   /www/wwwroot/yuanwuzhi-website/
   ```

3. 用 Nginx 指向该目录。

4. 域名解析到服务器 IP，后续再配置 HTTPS 证书。

更详细步骤见：

[腾讯云部署说明](./docs/tencent-cloud-deploy.md)

上线前确认事项见：

[官网上线前待确认清单](./docs/prelaunch-checklist.md)

## 当前内容边界

- 元小鲲公开首要卖点：浸没式液冷、低噪、实验室部署、元Space 管理、小型集群。
- 暂不公开：固定配置、价格、未确认版本、未验证能力、客户真实名称。
- 客户实践页面先保留脱敏案例位置，后续由 YUYU 补充。
- 联系方式、公司主体、地址、备案信息上线前需要最终确认。

## 重要素材

素材目录：

```text
public/assets/
```

当前包含：

- `xiaokun-hero-render.png`：元小鲲首页主视觉
- `xiaokun-original-reference.png`：浸没式一体机原始参考图
- `yuanspace-login.png`：元Space 登录页截图
- `yuanspace-dashboard.png`：元Space 概览截图
- `yuanspace-groups.png`：元Space 课题组管理截图
- `yuanspace-task.png`：元Space 计算任务截图

## 后续待补

- 替换为正式 Logo SVG / 透明 PNG。
- 补充公司电话、邮箱、地址、公众号二维码。
- 迁移旧官网新闻活动、媒体报道、加入我们内容。
- 对接旧官网产品查询或新技术支持入口。
- 补充脱敏客户实践。
