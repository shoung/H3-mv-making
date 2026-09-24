# H3-mv-making

以歌曲、歌詞或 LRC 規劃劇情型真人 MV 的 Codex Skill。它會產出故事與分鏡、角色／場景／道具及逐鏡關鍵幀的中英文圖片提示詞、MiniMax H3 的中英文影片提示詞，以及繁體中文桌面版 HTML 製作計劃。

> 此倉庫提供**製作計劃與提示詞**，不會自行產生圖片、影片或完成剪輯。生成結果仍需人工檢查，鏡頭時間也應在剪輯時對齊實際唱句與音樂事件。

## 來源與改動

本 Skill 改寫自 [mxfo998-web/h3-music-mv-master-v0-1](https://github.com/mxfo998-web/h3-music-mv-master-v0-1)，原始構想與基礎工作流程出自該倉庫作者。請先閱讀原倉庫及其後續更新。這個倉庫是獨立改作，並非原作者或 MiniMax 官方發行版本。

相較於原版本，這裡主要做了以下調整：

- 移除對 `minimax-h3-digital-human-director-v0-2` 的必要依賴，將故事、真人表演和導演曲線整理進本 Skill 的參考文件。
- 對齊 MiniMax 官方 [`h3-prompt-writing`](https://github.com/MiniMax-AI/MiniMax-H3/tree/main/skills/h3-prompt-writing) 的 H3 英文提示詞結構，並訂出明確的格式優先規則。
- 每份圖片及 H3 提示詞提供繁體中文、英文兩版；繁體中文 H3 是語意對照版，英文版使用官方欄位與首幀引用格式。
- 最終 HTML 改為繁體中文、僅供桌面瀏覽；精簡重複規則及頁面功能。
- 明確區分「已寫好的提示詞」與「尚待生成、人工確認的圖片／影片」。

## 安裝

將本倉庫的 `h3-music-mv-master-v0-1` 資料夾放進目標專案的 `.agents/skills/`。此位置讓 Skill **只供該專案使用**。

```text
你的專案/
└─ .agents/
   └─ skills/
      ├─ h3-music-mv-master-v0-1/
      │  ├─ SKILL.md
      │  └─ references/
      └─ h3-prompt-writing/
         ├─ SKILL.md
         └─ references/
```

另需從 [MiniMax-H3 官方倉庫](https://github.com/MiniMax-AI/MiniMax-H3/tree/main/skills/h3-prompt-writing) 安裝 `h3-prompt-writing` 至同一個 `.agents/skills/` 目錄。本倉庫沒有重新分發該官方 Skill。`simple-story-mv-maker` 和 `gpt-image-2-cinematic-frames` 不是啟動條件；若自行安裝，只能作為額外參考。

安裝後，確認代理程式能讀到兩份 `SKILL.md`。若你的代理程式使用不同的專案 Skill 路徑，請依其設定放置，並維持兩個 Skill 位於同一層。

## 使用方法

提供歌曲音檔及歌詞或 LRC，並指定使用本 Skill，例如：

> 請使用 `h3-music-mv-master-v0-1`，依這首歌曲與歌詞製作劇情型真人 MV 計劃。輸出繁體中文桌面版 HTML，圖片與 H3 提示詞各提供繁體中文和英文版。

可另外指定故事題材、角色、場景、畫幅或視覺風格。若要精確卡詞，建議提供 LRC 或其他可靠時間碼。

建議按以下順序執行：

1. 核對歌詞與音檔，規劃歌曲段落、故事與鏡頭時間表。
2. 根據資產提示詞製作角色身份、場景及道具參考圖，再產出每鏡的獨立關鍵幀。
3. 人工檢查身份、服裝、道具、支撐姿勢與光線的連續性。
4. 將單鏡關鍵幀作為 H3 I2VA 的 `<Picture 1>`，使用該鏡英文 H3 提示詞生成影片。
5. 將原歌曲置於後期時間軸，依唱句和動作調整切點、聲音及淡出。

預設每個 H3 生成單元是一個獨立、連續的 4–15 秒鏡頭，畫幅為 16:9；實際可用時長、解析度與模式仍以使用的生成介面為準。

## 注意事項

- `P`、`D`、`K`、`S`、`A` 是本 Skill 的導演規劃代碼，不是 MiniMax H3 的 API 參數。定義見 [`global-director-score.md`](h3-music-mv-master-v0-1/references/global-director-score.md)。
- `C`、`S`、`P` 加數字是角色、場景、道具資產編號；`KF-xx` 是對應鏡頭的關鍵幀編號。編號只是製作索引，不代表圖片已存在。
- H3 提示詞中的歌曲預設由後期加入，`non_diegetic_music` 設為 `N/A`。請按實際製作方式調整音訊流程。
- 提供歌曲、歌詞、圖像或角色設定時，請確認你有相應的使用權；不要把私人音檔或未授權素材直接提交至公開倉庫。
- 原倉庫與 MiniMax 官方倉庫各自保有其內容及權利。本倉庫未附加原倉庫的授權聲明；使用或再散布原作者內容前，請自行確認其授權條件。

## 檔案

- [`h3-music-mv-master-v0-1/SKILL.md`](h3-music-mv-master-v0-1/SKILL.md)：工作邊界、優先規則與主流程。
- [`h3-music-mv-master-v0-1/references/`](h3-music-mv-master-v0-1/references/)：歌曲拆解、導演曲線、連續性、H3 雙語格式、HTML 結構及交付檢查。
