# 無障礙出行助手 / Accessibility Travel Assistant

九龍塘無障礙步行導航 — 為長者及輪椅使用者而設。SDG 10 + SDG 11。

**網站：** https://calvinlam85.github.io/navi/

## 這個 repo 是什麼

`navi.html`、`index.html` 同 `data/` 係**自動複製出嚟**嘅發佈副本，唔係原稿。
`index.html` 係 `navi.html` 嘅 byte-identical 副本 —— 因為 GitHub Pages 只會喺根目錄
用 `index.html` 做首頁，冇咗佢短網址會 404；`navi.html` 就係你叫嘅名。兩個都由
發佈 script 一次過產生，所以永遠唔會唔同。
原稿喺本機嘅 `accessibility-navigator.html`（連埋 Python pipeline、測試同文件）。
改完原稿之後，喺原稿個資料夾雙擊 `發布到網站.bat`，呢個 repo 就會更新，
GitHub Pages 大約一分鐘後自動重新部署。

**唔好喺呢個 repo 直接改嘢** —— 下次發佈會覆蓋，改動會靜靜咁消失。

## 內容

| 檔案 | 用途 |
|---|---|
| `index.html` | 整個 App（CSS / JS / SVG 全部內嵌，單一檔案） |
| `data/kt_graph.js` | 行人路網圖：14,322 節點 / 15,576 條邊（政府 3D 行人網絡） |
| `data/kt_facilities.js` | 236 個無障礙設施（升降機 60 / 斜道 44 / 有蓋通道 132） |
| `data/kt_landmarks.js` | 18 個地標 |
| `data/kt_pois.js` | 301 個商戶 POI |

全部路線規劃（A*）、設施配對同語音旁白都喺瀏覽器本機完成 —— 冇 Directions API、
冇 AI 服務、冇地理編碼。上網只係為咗 Mapbox 圖磚同 Google 字型。

## 注意

`index.html` 內含一個 Mapbox **public** token（`pk.` 開頭）。Public token 本來就係
設計成放喺前端、公開看得見嘅，唔算洩漏；但佢冇設定 URL 限制，即係任何網站都可以
用佢去載入地圖，會消耗帳戶額度。若要收窄，可以喺 Mapbox 帳戶為 token 加上
allowed URLs（記得同時容許 `http://localhost:8080`，唔係本機開發會爆 403）。
