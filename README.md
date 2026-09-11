# 強震モニタ風地震シミュレーション

TurboWarp（Scratch）で動作する、日本向けの地震・緊急地震速報（EEW）シミュレータです。震源・規模・深さ・発生タイミングを変えながら、P波/S波の伝播、震度分布、EEW の発報、津波警報などを確認できます。

---

## 操作方法

| 操作 | 内容 |
| --- | --- |
| ← / → | マグニチュード（M1〜M12） |
| ↑ / ↓ | 震源の深さ（0〜1000km） |
| Q / W | 発生タイミング（0〜300秒） |
| A | 地震イベント開始を主要動到達に合わせる |
| スペース / 開始ボタン | シミュレーション開始 |
| マウスホイール | 地図ズーム |
| R | カメラリセット |

## 画面構成

- 地図と観測点、情報パネル、左上の緊急地震速報（EEW）パネルで構成されます。
- 画面左下の設定パネルで規模・深さ・タイミングを調整します。
  - シミュレーション開始と同時に設定パネルは隠れます。
  - 再度調整するときは左下の「設定」を押すと表示されます。右上の「×」で閉じられます。
  - パネル上部に震央と経過秒数を表示します。
- EEW 発表中は、推定震央が左上の EEW パネルに表示されます。
- 停止すると設定パネルが戻ります。

## 主な機能

- 規模・深さ・発生タイミングのリアルタイム調整（M1〜M12 / 0〜1000km / 0〜300秒）
- P波・S波の伝播と到達時刻の計算
- 観測点ごとの震度推定と震度分布の表示
- 緊急地震速報（EEW）の推定震源・予想最大震度
- 津波警報・津波予報のシミュレーション
- 読み上げ・効果音

## デプロイ

### Cloudflare Pages

1. リポジトリを fork / clone する
   ```
   git clone https://github.com/walbcglgh/JapanEewSimulator.git
   ```
2. Cloudflare Pages で「Create a project」→「Connect to Git」からこのリポジトリを選択する
3. ビルド設定
   - Build command: なし
   - Build output directory: `/`
   - Environment variables: なし
4. 「Save and Deploy」で公開する

### ローカルでの確認

`index.html` を直接開くと `fetch` がブロックされ、プロジェクトデータ（`quake-sim-data.bin`）を読み込めません。必ず HTTP サーバー経由で開いてください。

```
python -m http.server 8000
```

ブラウザで `http://localhost:8000` を開きます。

## ファイル構成

| ファイル | 内容 |
| --- | --- |
| `index.html` | 起動画面・ローダー・操作パネル（HTML側のUI） |
| `quake-sim-data.bin` | 実行時に読み込むプロジェクト本体（zip: `project.json` とアセット） |
| `project.json` | プロジェクト本体の単体コピー（実行時は `quake-sim-data.bin` を使用） |
| `CNAME` | 公開ドメイン設定 |

## 注意事項

- 地震・津波のシミュレーションは簡略化した計算を用いており、実際の現象とは異なります。
- 音声（読み上げ・効果音）が含まれます。音量に注意してください。
- ブラウザの設定によっては一部機能が制限される場合があります。

## ライセンス

- TurboWarp Packager: Mozilla Public License 2.0
- Scratch: MIT License
- 本プロジェクト: 改善版として配布

## 参考

- TurboWarp: https://turbowarp.org
- 元プロジェクト: https://turbowarp.org/1220818872
- Scratch: https://scratch.mit.edu
- Cloudflare Pages: https://developers.cloudflare.com/pages/

## クレジット

- 元プロジェクト作成者: TurboWarp / Scratch コミュニティ
- UI 調整・改修: walbcglgh

最終更新: 2026年9月

---

# 強震監視器風地震模擬器

以 TurboWarp（Scratch）製作、面向日本地震與緊急地震速報（EEW）的模擬器。可調整震源、規模、深度與發生時間，觀察 P 波／S 波傳播、震度分布、EEW 發布與海嘯警報等。

---

## 操作方式

| 操作 | 內容 |
| --- | --- |
| ← / → | 調整地震規模（M1〜M12） |
| ↑ / ↓ | 調整震源深度（0〜1000km） |
| Q / W | 調整發生時間（0〜300 秒） |
| A | 讓地震事件開始與主要波到達同步 |
| 空白鍵 / 開始按鈕 | 開始模擬 |
| 滑鼠滾輪 | 地圖縮放 |
| R | 重設相機 |

## 畫面說明

- 由地圖與測站、資訊面板，以及左上方的緊急地震速報（EEW）面板組成。
- 左下角設定面板可調整規模、深度與發生時間。
  - 開始模擬時設定面板會自動隱藏。
  - 需要再調整時，點左下角「設定」即可展開；按右上角「×」收起。
  - 面板上方顯示震央與經過秒數。
- EEW 發布期間，預估震央會顯示在左上方的 EEW 面板。
- 按停止後，設定面板會回來。

## 主要功能

- 即時調整規模、深度與發生時間（M1〜M12 / 0〜1000km / 0〜300 秒）
- P 波、S 波傳播與到達時刻計算
- 各測站震度估算與震度分布顯示
- 緊急地震速報（EEW）的推定震源與預估最大震度
- 海嘯警報與海嘯預報模擬
- 語音朗讀與音效

## 部署

### Cloudflare Pages

1. Fork / clone 本倉庫
   ```
   git clone https://github.com/walbcglgh/JapanEewSimulator.git
   ```
2. 在 Cloudflare Pages 點「Create a project」→「Connect to Git」，選擇本倉庫
3. 建置設定
   - Build command: 無
   - Build output directory: `/`
   - Environment variables: 無
4. 點「Save and Deploy」發布

### 本機測試

直接用瀏覽器開啟 `index.html` 會被 `fetch` 限制，無法載入專案資料（`quake-sim-data.bin`）。請務必透過 HTTP 伺服器開啟。

```
python -m http.server 8000
```

瀏覽器開 `http://localhost:8000`。

## 檔案結構

| 檔案 | 內容 |
| --- | --- |
| `index.html` | 啟動畫面、載入器與操作面板（HTML 端 UI） |
| `quake-sim-data.bin` | 執行時載入的專案本體（zip：內含 `project.json` 與素材） |
| `project.json` | 專案本體的單獨複本（執行時使用 `quake-sim-data.bin`） |
| `CNAME` | 公開網域設定 |

## 注意事項

- 地震與海嘯模擬採用簡化計算，與實際現象不同。
- 含語音（朗讀與音效），請注意音量。
- 依瀏覽器設定，部分功能可能受限。

## 授權

- TurboWarp Packager: Mozilla Public License 2.0
- Scratch: MIT License
- 本專案: 以改善版本發布

## 參考

- TurboWarp: https://turbowarp.org
- 原始專案: https://turbowarp.org/1220818872
- Scratch: https://scratch.mit.edu
- Cloudflare Pages: https://developers.cloudflare.com/pages/

## 致謝

- 原始專案作者: TurboWarp / Scratch 社群
- UI 調整與改修: walbcglgh

最後更新: 2026 年 9 月

---

# Japan Earthquake Simulator (Kyou-shin Monitor Style)

A Japan-focused earthquake and Earthquake Early Warning (EEW) simulator built with TurboWarp (Scratch). You can change the hypocenter, magnitude, depth and timing, and observe P/S wave propagation, seismic intensity distribution, EEW issuance and tsunami warnings.

---

## Controls

| Input | Action |
| --- | --- |
| Left / Right | Magnitude (M1–M12) |
| Up / Down | Hypocenter depth (0–1000 km) |
| Q / W | Occurrence time (0–300 s) |
| A | Sync the earthquake event with main-wave arrival |
| Space / Start button | Start the simulation |
| Mouse wheel | Zoom the map |
| R | Reset the camera |

## Screen Layout

- The screen consists of the map with stations, an information panel, and the EEW panel in the top-left.
- The settings panel in the bottom-left adjusts magnitude, depth and timing.
  - The settings panel hides automatically when the simulation starts.
  - To adjust again, click "設定" in the bottom-left to reopen it; click "×" in the top-right to close it.
  - The top of the panel shows the epicenter and elapsed seconds.
- While an EEW is active, the estimated epicenter is shown in the top-left EEW panel.
- Pressing Stop brings the settings panel back.

## Features

- Real-time adjustment of magnitude, depth and occurrence time (M1–M12 / 0–1000 km / 0–300 s)
- P-wave and S-wave propagation and arrival-time calculation
- Per-station intensity estimation and intensity distribution display
- EEW estimated hypocenter and predicted maximum intensity
- Tsunami warning / advisory simulation
- Speech readout and sound effects

## Deployment

### Cloudflare Pages

1. Fork / clone the repository
   ```
   git clone https://github.com/walbcglgh/JapanEewSimulator.git
   ```
2. In Cloudflare Pages, click "Create a project" → "Connect to Git" and select this repository
3. Build configuration
   - Build command: none
   - Build output directory: `/`
   - Environment variables: none
4. Click "Save and Deploy"

### Local Testing

Opening `index.html` directly is blocked by `fetch`, so the project data (`quake-sim-data.bin`) cannot be loaded. Always open it through an HTTP server.

```
python -m http.server 8000
```

Then open `http://localhost:8000`.

## Files

| File | Description |
| --- | --- |
| `index.html` | Launch screen, loader and control panel (HTML-side UI) |
| `quake-sim-data.bin` | Project loaded at runtime (zip: `project.json` plus assets) |
| `project.json` | Standalone copy of the project (runtime uses `quake-sim-data.bin`) |
| `CNAME` | Public domain setting |

## Disclaimer

- The earthquake and tsunami simulations use simplified calculations and differ from real phenomena.
- Speech readout and sound effects are included; mind the volume.
- Some features may be restricted depending on browser settings.

## License

- TurboWarp Packager: Mozilla Public License 2.0
- Scratch: MIT License
- This project: distributed as an improved version

## References

- TurboWarp: https://turbowarp.org
- Original project: https://turbowarp.org/1220818872
- Scratch: https://scratch.mit.edu
- Cloudflare Pages: https://developers.cloudflare.com/pages/

## Credits

- Original project author: TurboWarp / Scratch community
- UI adjustments and revisions: walbcglgh

Last updated: September 2026
