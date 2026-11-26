# Gemini 生图 & Veo/可灵/即梦 图生视频提示词规范

本规范专为零基础新手稳定产出**高一致性、少穿帮、接近 @GhibliDayss 质感**的动画短片而设计。

---

## 零、资产定妆图与空景图生图公式（首套创建 & 按剧情按需补画通用）

无论是零基础创建第一套主角图，还是**先定好新一期剧情后、按需补画这一期新增的场景空景图或宠物图**，都使用这一组模板在 Gemini 生图。

> **画风统一铁律**：只要 `01_资产库/01_角色参考图/` 里已经有了主角图（例如 `01_资产库/01_角色参考图/主角_女孩_定妆图.jpg`），之后每次按剧情补画新场景或新宠物时，**都把主角图一并上传到 Gemini 当作画风参考**，这样所有分镜里的角色、宠物和房间画风会 100% 统一。

### 1. 主角定妆图模板（存为 `01_资产库/01_角色参考图/主角.png`）
- **核心要求**：单人、正面或微侧面半身/全身、光线柔和均匀、背景简单不抢戏、服装轮廓和发色一目了然，方便后续每镜垫图复用。
- **英文模板**：
  `Warm nostalgic 2D hand-drawn Japanese anime character design sheet, gentle cel-shading with soft dark-brown ink outlines, watercolor aesthetic. A [年龄与性别，如 young East Asian woman in her early 20s] with [发型发色，如 messy dark brown bob hair tied half-up] and warm gentle eyes, wearing [固定穿搭，如 an oversized cream knit sweater and an olive green linen apron]. Standing naturally in a relaxed pose, soft warm indoor light, clean simple warm-beige background, clear full upper-body view, no text, no watermark.`

### 2. 宠物定妆图模板（可选，存为 `01_资产库/01_角色参考图/<宠物名>.png`）
- **英文模板**：
  `Warm nostalgic 2D hand-drawn Japanese anime illustration style, soft dark-brown ink outlines, watercolor texture. A cute [品种与毛色，如 chubby ginger tabby cat with white paws] wearing [配饰，如 a small soft red fabric collar], sitting calmly with gentle expressive eyes. Soft warm daylight, clean simple cream background, full body visible, no text, no watermark.`

### 3. 核心场景空景图模板（存为 `01_资产库/02_核心场景图/<场景名>.png`）
- **核心要求**：必须是**无人空景**（`empty room, no people`），把窗户、灶台/书桌、灯光位置定死；**生图时建议同时上传刚才生成的 `主角.png`**，并在 Prompt 开头加上画风锁定句，让人物和房间的画风彻底一致。
- **英文模板（16:9 横屏版，若做竖屏将末尾改为 `9:16 vertical aspect ratio`）**：
  `Use the uploaded character image ONLY as a visual style, line-art, and color-palette reference; DO NOT include any person or character in this scene. Warm nostalgic 2D hand-drawn Japanese anime background illustration, lush watercolor painted interior, soft dark-brown ink outlines. Empty cozy [房间类型，如 small wooden Japanese home kitchen] with NO people and NO characters. On the left is a [窗户设定，如 large wooden-framed window showing soft twilight sky]; in the center-right is [核心家具/灶台，如 a warm wooden countertop, small gas stove with a ceramic pot, hanging brass utensils, and ceramic bowls on open shelves]; lit by a warm amber pendant lamp. Cinematic wide establishing view, 16:9 widescreen aspect ratio, clean illustration, no text, no watermark.`

---

## 一、Gemini 垫图生图公式（保持角色与场景不跑偏）

在 Gemini 网页端生图时，每次先上传本镜需要的参考图（角色图 + 场景图，连续特写镜还要加上一镜刚生好的图），然后复制英文 Prompt。

### 标准结构（6 段式）
`[画风锚定] + [参考图强绑定指令] + [景别与机位] + [主体动作与神态] + [环境氛围与冷暖光影] + [画幅与去水印后缀]`

### 常用模块词库
1. **画风锚定（固定开头）**：
   `Warm nostalgic 2D hand-drawn Japanese anime illustration style, gentle cel-shading with soft dark-brown ink outlines, lush watercolor painted background, cozy slice-of-life aesthetic.`
   *(注：不用生硬堆砌受保护电影名或导演名，用具体笔触描述同样能出纯正手绘质感且更安全。)*

2. **参考图强绑定指令（紧跟开头，极其关键！）**：
   - **有角色 + 场景图时**：
     `Keep the exact same character design, hairstyle, hair color, and outfit from the character reference image. Keep the exact same room layout, furniture, window position, and interior details from the scene reference image.`
   - **有角色 + 场景图（按题材换装模式，当 `资产档案.md` 开启按题材换装时优先使用）**：
     `Keep the exact same face, facial features, hairstyle, and hair color from the character reference image, but dress the character in [本期专属温暖复古日系居家穿搭，例如 a soft oatmeal knit cardigan over a cream cotton blouse and warm brown linen trousers, no apron, wearing cozy indoor socks]. Keep the exact same room layout, furniture, window position, and interior details from the scene reference image.`
   - **只有景物特写（无人或仅局部手部）时**：
     `Keep the exact same kitchen countertop, utensils, lighting, and watercolor color palette from the scene reference image.`
   - **连续镜头「前镜垫后镜」（防锅具/食物/道具变样，强烈推荐！）**：
     当上一个镜头刚画出了某口锅、某盘切好的菜或某个杯子，下一镜继续拍它时，务必把上一镜生成的 `素材_图片/SXX.png` 一并传进 Gemini，并加上：
     `Continue directly from the previous shot reference image. Keep the exact same pot, bowl, utensils, food appearance, countertop texture, and warm lighting from the previous shot.`
     *(若连续镜头中也包含主角，请一并加上 `and the exact same outfit from the previous shot`，确保同一期内穿搭始终不跳戏。)*

3. **景别与机位词**：
   - 远景定环境：`Wide establishing shot`, `Exterior view looking through the warm window`
   - 中景叙事：`Medium shot`, `Waist-up shot`, `Over-the-shoulder shot`
   - 食物/手部特写：`Close-up shot`, `Top-down 45-degree angle close-up`, `Macro close-up of steaming pot`
   - 情绪空镜：`Atmospheric detail shot of raindrops on windowpane`

4. **冷暖光影对比词（治愈感核心）**：
   - `warm amber desk lamp glowing inside contrasting with cool deep-blue rainy twilight outside`
   - `soft golden morning sunlight streaming through sheer curtains, gentle dust motes`
   - `warm stove glow illuminating rising steam against a dim cozy evening room`

5. **画幅与去水印固定后缀（二选一，固定结尾）**：
   - **16:9 横屏（默认，适配 YouTube / B站）**：
     `cinematic composition, 16:9 widescreen aspect ratio, clean illustration, no text, no subtitles, no UI, no watermark.`
   - **9:16 竖屏（适配小红书 / 抖音）**：
     `cinematic vertical composition, 9:16 vertical aspect ratio, clean illustration, no text, no subtitles, no UI, no watermark.`

---

## 二、图生视频（I2V）提示词双版本模板

图生视频阶段最怕**画面乱扭、人物突然开口说话、手指变成六根**。核心原则：**只让局部环境和微动作动起来，镜头只做极慢的推拉摇移**。

### 1. Google Veo 3 / 国际模型（英文模板）
**公式**：`[镜头微动] + [主体微动作] + [环境与物理动态] + [强制静音防人声后缀]`
- **示例（煮面特写）**：
  `Slow gentle camera push-in. The soup gently simmers with small rising bubbles, soft white steam drifting upward continuously. Subtle warm stove light flickering on the ceramic pot. Outside the blurred window, soft rain streaks fall quietly. Silent scene, no dialogue, no talking, no human voice, only soft ambient sound of simmering soup and gentle rain.`
- **示例（人物在桌边）**：
  `Static steady camera with very subtle breathing motion. The character gently blinks and smiles softly while looking down at the warm bowl, soft hair strands swaying slightly. Gentle steam rising from the cup on the table. Silent character, no dialogue, no speaking, no voice, only quiet cozy room ambience.`

> **Veo 3 两个核心小技巧**：
> 1. **为什么必须加 `Silent character, no dialogue, no talking, no voice`？** 像 Veo 3 等带原生音频的模型，如果画面里出现人物，极易自作聪明生成英文对白。加上这句能大幅压低乱说话概率。
> 2. **原生环境音可以直接留用！** 结尾的 `only soft ambient sound of ...` 会引导 Veo 3 生成雨声、冒泡声、煎炸声。如果生成的片段声音干净自然且没人说话，在剪映里可以直接保留原声（音量调至 `-12dB ~ -18dB`），省去再去到处找音效！

### 2. 可灵（Kling）/ 即梦（Jimeng）/ 海螺（中文模板）
**公式**：`[镜头运动] + [主体克制微动] + [环境与光影微动] + [画风稳定声明]`
- **示例（煮面特写）**：
  `镜头极缓慢地向前推进。锅里的热汤微微咕嘟冒泡，白色热气缓缓向上飘散，厨房暖黄灯光在锅沿轻微闪烁，背景窗玻璃上雨滴缓慢滑落。画面保持细腻温暖的手绘二维动画质感，不要出现多余文字或大幅变形。`
- **示例（人物在桌边）**：
  `固定机位轻微呼吸感镜头。人物保持安静坐姿，轻轻眨眼并露出温柔微笑，发丝随微风轻轻晃动，面前的热汤持续冒出柔和白烟，窗外细雨缓缓落下。保持角色五官与服装完全稳定，无大幅动作。`

> **可灵 / 即梦「首尾帧」省事小贴士**：
> 如果相邻两镜（例如 `S04` 刚下料入锅 → `S05` 汤滚冒泡）之间画面角度接近，可以在可灵或即梦开启**「首尾帧」**模式，把 `S04.png` 放首帧、`S05.png` 放尾帧，生成一条自然过渡的 5 秒视频，连贯性极佳。

---

## 三、新手高频 AI 穿帮避坑指南

1. **吃东西/拿筷子特写很容易多手指或筷子变弯**：
   - **解法**：尽量避免“手指正面捏着细筷子夹起细面条往嘴里送”的复杂连续动作；改用**“侧后方过肩视角看热气腾腾的碗”**、**“端起温热茶杯双手捧着微笑”**、或**“勺子舀起一勺浓汤的极简特写”**。
2. **不要在一镜里塞超过 2 个动作**：
   - 错误示范：人物走到窗边关窗，然后转身走回灶台开火并打蛋。
   - 正确示范：一镜只做 1 件事——“人物站在灶台前轻轻搅动汤勺，蒸汽缓慢上升”。
3. **规避版权敏感词**：
   - 永远不要在 Prompt 中写 `Totoro`、`Chihiro`、`Spirited Away`、`Hayao Miyazaki`、`Studio Ghibli logo` 等具体版权实体名；统一用 `Studio Ghibli inspired` 或纯画风描述词 `warm nostalgic 2D hand-drawn anime style, soft dark-brown outlines, watercolor background`。
