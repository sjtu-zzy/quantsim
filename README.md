# QuantSim

一个无需构建工具的单文件 AI 量化交易模拟器。它使用虚拟资金进行美股、A 股与加密货币的行情查看、手动交易和 AI 自动交易。

## 运行

推荐使用本地 HTTP 服务打开，避免浏览器对外部行情接口的限制：

```powershell
python -m http.server 8080
```

随后访问 `http://127.0.0.1:8080/QuantSim.html`。

也可访问已经部署好的在线链接`https://quantsim.pages.dev/`。

## 功能

- 虚拟账户、持仓、手续费、交易历史与浏览器本地持久化。
- 美股、A 股、BTC/ETH 行情，以及每个标的的趋势图。
- 手动交易与 AI 自动交易，自动交易频率可配置。
- AI 分析摘要会显示在主界面的 AI 状态卡中。
- A 股以 CNY 报价，账户、现金与总资产统一以 USD 结算，并按 USD/CNY 汇率折算。

## 行情数据源

| 市场 | 数据源 | 配置 |
| --- | --- | --- |
| 美股 | Finnhub | 在“AI 分析”面板填写 Finnhub API Key。未配置时将使用模拟数据。 |
| A 股 | 腾讯财经 | 默认直连；若浏览器限制跨域，可在 `QuantSim.html` 顶部设置 `PROXY_URL` 为自己的代理前缀。 |
| 加密货币 | Binance | 使用公开 API，无需 Key。 |

当数据源不可用时，页面会明确标注“模拟”并使用模拟行情作为兜底。

## AI 配置与安全

在“AI 分析”面板中填写兼容 OpenAI Chat Completions 的 API 地址、模型与密钥。页面会请求 JSON Mode，并仅接受 JSON 决策结果。

API Key 和 Finnhub Key 仅保存在当前浏览器的 `localStorage`，不会写入此仓库。请不要将密钥直接写入 `QuantSim.html`、`.env` 之外的任何受版本控制文件，或提交到 GitHub。

## 文件

- `QuantSim.html`: 完整应用，直接用浏览器打开即可。

## 免责声明

本项目是交易模拟工具，不构成投资建议。公开行情接口可能存在延迟、限流或不可用情况。
