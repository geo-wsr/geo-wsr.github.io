# 杜能圈交互实验室

独立静态站点，发布地址：

<https://geo-wsr.github.io/>

本站不依赖后端，所有竞租、交通影响、多城市竞争和集约程度计算均在浏览器中完成。

更新线上版本时，在源码目录执行：

```powershell
npm run build:release
```

然后将 `release/` 中的静态文件复制到本仓库根目录，并重新提交。

## 安全

页面通过 `<meta http-equiv="Content-Security-Policy">` 限制资源来源（GitHub Pages 不支持自定义响应头）。
修改 CSP 时请注意两处依赖，否则会静默劣化页面效果：

- `style-src` 必须保留 `'unsafe-inline'`：KaTeX 依赖大量内联 style 属性。
- `font-src` 必须包含 `data:`：KaTeX_Size3 的 woff2 被构建内联为 data URI。

另需留意：本仓库根目录即线上发布目录，任何提交到这里的文件都会以
`https://geo-wsr.github.io/<文件名>` 公开可访问，建议不要放置内部路径等非发布内容。
