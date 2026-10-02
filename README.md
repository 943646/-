# 全球海拔与海深离线查询系统

三维地球上查询任意位置的海拔 / 海深，数据全部本地内置，不依赖网络。

- 在线访问：https://943646.github.io/earth-elevation/
- 单文件离线版：[`earth-offline.html`](earth-offline.html)，下载后双击即可使用，无需网络

## 文件结构

| 路径 | 说明 |
|---|---|
| `index.html` | 网页版（界面与程序），数据从下面的文件加载 |
| `lib/three.min.js`、`lib/OrbitControls.js` | three.js 三维引擎 |
| `data/land.jpg`、`data/sea.jpg` | 陆地海拔 / 海洋深度贴图（sqrt 编码，约 5 km 网格） |
| `data/mask.png` | 海陆掩膜 |
| `data/ext.webp` | 极值网格：每格（约 20 km）最高点 / 最深点，16 位无损 |
| `data/countries.json` | Natural Earth 10m 国界（TopoJSON） |
| `earth-offline.html` | 由构建脚本生成的单文件离线版（所有文件内嵌） |
| `tools/build_offline.py` | 生成单文件离线版的脚本 |

## 修改后重新生成离线版

修改 `index.html`、`lib/` 或 `data/` 后运行（需要 Python 3）：

```
python3 tools/build_offline.py
```

## 数据来源

- 地形 / 海深：AWS Terrain Tiles（SRTM · GMTED · ETOPO1 · GEBCO）
- 国界：Natural Earth 10m（经 world-atlas）
- 经典位置：各高峰、海沟等的官方测量值
