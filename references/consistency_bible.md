# 漫剧一致性手册模板（Consistency Bible · 漫画版）

> 锁定后，后续所有生图 prompt、视频 prompt 只引用「ID + 锁定描述 + 设定图」，外观不再改写。
> 这是保证「同一角色 / 场景 / 道具 / 画风跨分镜一致」的唯一权威来源。
> 漫剧是「画出来的」，AI 生图比真人短剧更容易「长新脸、换发色、串画风」，所以本手册比真人版锁得更狠：**每个角色必须有实生设定图 + 表情表 + 色卡**。

---

## 〇、画风锁定（全剧唯一，最先写）

- **画风名**：国漫2D / 日漫赛璐璐 / 韩漫条漫（见 `references/art_styles.md`）
- **画风关键词**：`<从 art_styles.md 对应预设原样粘贴，全程不变>`
- **全剧色调**：一句话描述主色调（如「金红黑，浓墨重彩」/「低饱和高级灰+窗光」）

> 下面所有生图 prompt 都必须先带上「画风关键词」，再带资产描述。

---

## 一、人物 CHAR-NN

每个角色写一个完整卡片，并**实际生成一张三视图设定图**（通过 ImageGen）。

- **ID**：CHAR-01
- **姓名**：顾辰
- **锁定描述**：28 岁，冷峻黑发短发，剑眉星目，左颊一道淡刀疤，常着玄黑锦袍金纹，气质疏离，身形挺拔
- **色卡（防换色）**：发色=纯黑，瞳色=深褐，肤色=冷白，主服色=玄黑+金纹
- **表情扩展表（防表情跑偏，至少锁定 5 个）**：
  | 表情 | 锁定关键词（生图时按需引用） |
  |------|------------------------------|
  | 常态 | calm cold expression, sharp gaze |
  | 愤怒 | fierce angry eyes, clenched jaw, veins |
  | 悲伤 | downcast eyes, furrowed brows, silent grief |
  | 震惊 | widened eyes, parted lips, shock |
  | 得意/冷笑 | cold smirk, condescending sneer |

- **人物详细描述词（正向提示词）**：
  `<画风关键词>, a 28-year-old Chinese man, cold handsome face, short black hair, sharp eyebrows, star-like eyes, a faint scar on left cheek, wearing black gold-embroidered robe, aloof aura, tall and straight posture, highly detailed`

- **三视图设定图（实生图，必须生成）**：
  - 提示词：`<画风关键词>, character reference sheet, three views, front view + side view + back view, full body, standing straight, <锁定描述>, plain light grey background, character sheet layout, consistent face across three views`
  - size：`1536x1024`（横版三格）
  - **生成后把图片路径记在这里**，作为后续分镜图的一致性参考图（可用于图生图 image1 参考）。

---

## 二、场景 SCENE-NN

- **ID**：SCENE-01
- **名称**：顾氏古宅大厅
- **锁定描述**：明清古风木质大厅，红木立柱，烛光昏黄，地面青砖，背景水墨屏风，岁月感
- **三视图提示词（全景 / 中景 / 特写）**：
  - 全景：`<画风关键词>, establishing wide shot of SCENE-01, ancient Chinese wooden hall, red columns, dim candlelight, blue brick floor, ink screen, <锁定描述>`
  - 中景：`<画风关键词>, medium shot of SCENE-01, showing pillars and candlelit space, <锁定描述>`
  - 特写：`<画风关键词>, close-up of SCENE-01 detail, candle on red wood, texture of blue brick, <锁定描述>`
- **场景设定图（实生图，建议生成）**：size `1024x1536`，竖屏 9:16 构图，生成后记录路径。
- **时间变体**：若场景分白天/夜晚，记为 `SCENE-01-day` / `SCENE-01-night`，分别锁定光影并各自生成设定图。

---

## 三、道具 PROP-NN

- **ID**：PROP-01
- **名称**：龙纹玉佩
- **锁定描述**：羊脂白玉，雕五爪金龙，绳结朱红，约掌心大小
- **三视图提示词（正面 / 侧面 / 背面）**：
  - 正面：`<画风关键词>, front view of PROP-01, white jade pendant carved with golden five-clawed dragon, red string, <锁定描述>`
  - 侧面：`<画风关键词>, side view of PROP-01, thickness of jade, carving depth, <锁定描述>`
  - 背面：`<画风关键词>, back view of PROP-01, plain jade back, red string knot, <锁定描述>`
- **道具设定图**：可选，size `1024x1024`。

---

## 使用约定

1. 每个资产生成后，把「锁定描述」「色卡」「表情表」「三视图提示词」「设定图路径」固化进本手册。
2. Stage 6 / Stage 7 的提示词里，角色只写 `CHAR-01 (<锁定描述关键短语>)`，**不重写长相、不换发色瞳色**；生图时可直接用已生成的设定图做 `image1` 参考图来强锁脸。
3. 一个角色多套服饰 → `CHAR-01-A（常服）` / `CHAR-01-B（战袍）`，分别锁定并分别生成设定图。
4. **画风关键词全程一字不改**，任何一张图串了别的画风立即重生成。
