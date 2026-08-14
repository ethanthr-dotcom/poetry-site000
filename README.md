# 诗泉 · 本地古诗词浏览器

收录 **371,313 首古诗词**，纯前端部署，无需服务器。

## 功能

- 随机展示一首古诗词
- 按作者、朝代、体裁筛选
- 数据完全在浏览器中加载，无后端依赖

## 本地预览

```bash
cd poetry-site
python3 -m http.server 8080
```

浏览器打开 http://localhost:8080/

## 部署到 GitHub Pages

### 1. 创建 GitHub 仓库

在 GitHub 上新建一个仓库（例如 `poetry-site`）。

### 2. 推送代码

```bash
cd poetry-site
git init
git add .
git commit -m "诗泉 · 古诗词浏览器"
git branch -M main
git remote add origin https://github.com/<你的用户名>/poetry-site.git
git push -U origin main
```

### 3. 开启 GitHub Pages

1. 打开仓库的 **Settings** → **Pages**
2. **Source** 选择 **Deploy from a branch**
3. **Branch** 选择 **main**，文件夹选 **/ (root)**
4. 点击 **Save**

等待 1-2 分钟，页面将上线：

```
https://<你的用户名>.github.io/poetry-site/
```

## 数据结构

```
poetry-site/
├── index.html          # 页面
└── data/
    ├── index.json       # 索引（161KB）
    ├── 001.json         # 75 个分块，每块约 5000 首
    ├── 002.json
    └── ...075.json      # 总计约 100MB
```

每个分块的诗词对象使用短键名：

| 键 | 含义 |
|---|---|
| `t` | 标题 |
| `a` | 作者 |
| `d` | 朝代 |
| `y` | 体裁 |
| `c` | 正文 |
