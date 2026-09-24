# MiniMax H3 雙語提示詞規則

本專案的 h3-prompt-writing/references/base-en.txt 與 MiniMax 官方同名參考檔一致。英文版依官方範本產出；繁體中文版是內容對照，方便閱讀與調整。

## I2VA 格式優先序

1. 保留官方首行，逐字使用：
   For the target video, at 0.00 seconds into the target video, <Picture 1> (from [Shot 1]) is fully referenced.
2. 首行後空一行，依序使用 integrated_multimodal_description、overall_soundscape、non_diegetic_music 三個欄位；欄位名、<Picture 1> 與 [Shot 1] 不翻譯。
3. 英文版欄位內容以英文撰寫。繁體中文版保留同一首行與欄位骨架，將欄位內容翻成繁體中文；原文歌詞、對白及可見文字維持用戶提供的語言。
4. 本 MV 預設每條提示詞只生成一個連續鏡頭。[Shot 1] 不加內部切點時間；下一鏡另起一份提示詞。絕對歌曲時間與 H3 生成時長寫在提示詞外的繁體中文製作說明。
5. <Picture 1> 是該鏡頭的精確首幀。提示詞先確立圖中可見的身份、服裝、構圖、支撐、接觸和光線，再敘述自然起動、主要動作及結束狀態。
6. integrated_multimodal_description 寫鏡頭中的同步動作聲；overall_soundscape 用一至四句連續文字概括環境聲、動作聲和非語言人物聲。原歌曲留待後期；兩版 non_diegetic_music 都固定寫 N/A。

## 英文正式版範例

以下僅示範結構，實際人物與場景應依歌曲和首幀重新撰寫。

For the target video, at 0.00 seconds into the target video, <Picture 1> (from [Shot 1]) is fully referenced.

integrated_multimodal_description: [Shot 1] <Picture 1> is the exact opening frame: a woman stands beneath a station awning, her right hand holding a closed umbrella and her weight settled on her left foot. She notices a letter on the bench, shifts her gaze and weight, then bends to pick it up with her free left hand. The paper rustles as her fingers close around it. The camera stays at eye level and moves in slightly as she reads the name. She straightens and holds the letter at chest height, looking toward the empty platform.

overall_soundscape: Light rain taps the awning and distant trains hum. The letter rustles once, with soft footsteps and a quiet breath near the camera.

non_diegetic_music: N/A

## 繁體中文對照版範例

For the target video, at 0.00 seconds into the target video, <Picture 1> (from [Shot 1]) is fully referenced.

integrated_multimodal_description: [Shot 1] <Picture 1> 是精確首幀：一名女子站在車站雨棚下，右手握著收起的雨傘，重心落在左腳。她注意到長椅上的信，先轉移視線與重心，再彎身以空出的左手拾起。手指握住紙張時發出輕微摩擦聲。攝影機維持視平高度，在她閱讀姓名時稍微靠近。她站直，把信拿到胸前，望向空蕩月台。

overall_soundscape: 細雨敲打雨棚，遠處列車傳來低鳴。信紙摩擦一次，近處有輕柔腳步聲與一口安靜的呼吸聲。

non_diegetic_music: N/A

## 對應與例外

- 兩版的首幀、角色身分、手部占用、空間路徑、主動作、攝影機、結束構圖與聲音事件逐項相同，不增減事件。
- 英文版是供官方 H3 格式使用的主要提示詞；繁體中文版標示為對照版。中文版本不是 MiniMax 官方的英文範本。
- 使用者改用 T2VA、FL2VA、L2VA 或 Ref2VA 時，先讀 h3-prompt-writing 的對應官方參考檔，依該模式的首尾幀對齊規則與欄位撰寫英文版，再建立繁體中文對照版。不得把 I2VA 首行套用到其他模式。
- 若使用者明確要求省略時間碼或改變欄位，該版本需標註為自訂格式，與官方格式版分開呈現。
