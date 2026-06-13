# 微信读书 16 型读书人格测试生成指令

你现在是我的「微信读书人格分析师 + 数据分析师 + 可视化设计师」。

请基于微信读书数据，为用户生成一份可分享的「16 型读书人格测试」报告。你需要调用微信读书 skill 拉取最新数据，分析读者的读书偏好、长期问题、困惑与解决路径、价值观画像，并生成结构化数据、Markdown 报告和 HTML 可视化页面。

注意：这不是 MBTI，也不是心理诊断。请只基于微信读书数据中的阅读行为、书籍主题、笔记、划线、想法、阅读时间线进行分析。不要空泛夸奖，不要过度推断；所有重要判断都要给出证据。

## 一、前置检查

1. 先检查当前环境是否已安装并可使用 `weread-skills`。
2. 如果没有安装或无法调用，请停止执行，并提示用户先安装微信读书 skill。
3. 不要要求用户在 prompt 中提供网盘、GitHub、微信读书账号密码、Cookie 或 token。
4. 如果需要图片资源，只使用公开可访问的图片 URL 或用户提供的本地文件路径。

## 二、数据获取要求

请调用微信读书 skill，尽可能获取以下数据：

1. 书架数据：
   - 已读、在读、想读书籍
   - 书名、作者、分类、简介
   - 阅读进度、读完时间、最近阅读时间
   - 书架数量必须按 `books.length + albums.length + (mp 非空 ? 1 : 0)` 计算

2. 阅读统计：
   - 总阅读时长
   - 年度/月度阅读变化
   - 读过、读完、阅读天数、笔记数量
   - 偏好分类、偏好作者、读得最多的书
   - 所有阅读时长字段都按秒处理，并展示为“X小时Y分钟”

3. 笔记与划线：
   - 有笔记的书籍列表
   - 每本书的划线数量、想法数量、书签数量
   - 具体划线内容
   - 我的想法、点评、书评
   - 高频关键词、反复出现的问题、反复认同或质疑的观点

如果数据量较大，可以分批处理，但不要只看最近几本书。请尽量覆盖完整阅读历史。

## 三、16 型读书人格模型

请使用以下 4 乘 4 模型。

横轴：读者主要通过阅读处理什么人生问题？

1. 自我安顿
   - 关注：我是谁、我如何理解自己、如何处理情绪、意义、孤独、自我怀疑。

2. 他人关系
   - 关注：人与人如何连接、相爱、伤害、误解、依赖、分离。

3. 社会秩序
   - 关注：权力、制度、阶层、性别、法律、国家、历史如何塑造人。

4. 未知未来
   - 关注：技术、AI、风险、经济、时代变化、不确定性会把人带向哪里。

纵轴：读者倾向于如何通过阅读处理这些问题？

1. 安顿型
   - 阅读用于慰藉、逃离、陪伴、情绪容器、精神安放。

2. 共情型
   - 阅读用于进入他人处境，理解人、命运、痛苦、爱与选择。

3. 建模型
   - 阅读用于拆结构、找机制、形成判断框架、理解系统如何运行。

4. 转化型
   - 阅读用于行动、修复、表达、创造、改变选择或现实处境。

## 四、16 型定义

请使用以下 16 型人格定义：

1. 内在避风港：自我安顿 + 安顿型。用阅读给自我搭一个临时住所，在书中获得安静、陪伴和情绪缓冲。
2. 内在回声者：自我安顿 + 共情型。借他人的生命经验听见自己，擅长从故事和心理文本中辨认内在感受。
3. 自我建模师：自我安顿 + 建模型。把情绪、习惯和选择拆成模式，试图建立理解自己的模型。
4. 生命改写者：自我安顿 + 转化型。把阅读当作改写人生脚本的工具，寻找可执行的改变路径。
5. 关系疗愈者：他人关系 + 安顿型。在阅读中处理亲密、依赖、分离和家庭带来的情绪。
6. 他心翻译者：他人关系 + 共情型。擅长进入他人处境，理解人如何相爱、误解、伤害和靠近。
7. 人性观察员：他人关系 + 建模型。把关系里的选择、操纵、信任和动机拆成可理解的人性机制。
8. 边界修复者：他人关系 + 转化型。从阅读中寻找修复关系和建立边界的行动方法。
9. 时代安放者：社会秩序 + 安顿型。在历史和时代叙事中安放个体处境，理解自己并非孤立承受。
10. 弱者看见者：社会秩序 + 共情型。对底层、女性、边缘者和被制度卷入的人保持敏感。
11. 制度解剖者：社会秩序 + 建模型。反复追问规则、权力、身份和结构如何塑造人的选择。
12. 现实改良者：社会秩序 + 转化型。关心制度如何变好，倾向把阅读转化为治理、法律、组织或公共行动方案。
13. 不确定安放者：未知未来 + 安顿型。借未来、科幻和趋势阅读处理时代变化带来的不安。
14. 技术人文守望者：未知未来 + 共情型。关心技术和未来会怎样改变人的处境、关系与尊严。
15. 风险建模师：未知未来 + 建模型。用认知、技术、经济和安全阅读训练风险判断与不确定决策。
16. 可能性开拓者：未知未来 + 转化型。把未来知识转化为技能、机会、创造和新的行动路径。

## 五、分类要求

请输出：

1. 主型人格：只能有 1 个。
2. 副型人格：必须有 3 个，从最像到最不像排序。
3. 每个主型/副型都要说明：
   - 得分或相对强度
   - 对应的问题域
   - 对应的处理方式
   - 关键证据书籍
   - 关键笔记/划线主题
   - 为什么它是主型或副型
4. 分析读者的读书偏好，并给出未来阅读建议。
5. 列出 16 型人格的完整介绍。

## 六、HTML 可视化要求

请生成 `reading-personality.html`。

页面必须包含：

1. 主型人格。
2. 3 个副型人格。
3. 读书偏好与未来阅读建议。
4. 长期问题。
5. 困惑与解决路径。
6. 价值观画像。
7. 16 型人格总览。

16 型人格总览必须做成 4 乘 4 坐标矩阵：

- 横轴：自我安顿、他人关系、社会秩序、未知未来。
- 纵轴：安顿型、共情型、建模型、转化型。
- 每个格子放 1 种人格。
- 4 个横轴问题域使用 4 种不同颜色。
- 页面上必须明确标注横轴和纵轴含义。
- 主型人格要在矩阵中高亮。
- 3 个副型人格要在矩阵中次级高亮。

建议颜色：

- 自我安顿：绿色 `#2f6f62`
- 他人关系：红色 `#a34842`
- 社会秩序：蓝色 `#305f89`
- 未知未来：金色 `#ad7a28`

## 七、人格卡通形象图片

本 prompt 已内置 16 张公开 GitHub 图片直链。执行时请优先使用下面的 `personality-assets.json` 清单，把对应图片填入 HTML；不要再要求用户额外上传图片。

图片仓库：

- GitHub 页面：`https://github.com/Shelro/WereadPersonalityTest/tree/main`
- Raw 直链前缀：`https://raw.githubusercontent.com/Shelro/WereadPersonalityTest/main/images/`

请生成或内置以下 `personality-assets.json`：

```json
{
  "内在避风港": "https://raw.githubusercontent.com/Shelro/WereadPersonalityTest/main/images/inner-harbor-abstract-v3.png",
  "内在回声者": "https://raw.githubusercontent.com/Shelro/WereadPersonalityTest/main/images/inner-echo-abstract-v3.png",
  "自我建模师": "https://raw.githubusercontent.com/Shelro/WereadPersonalityTest/main/images/self-modeler-abstract-v3.png",
  "生命改写者": "https://raw.githubusercontent.com/Shelro/WereadPersonalityTest/main/images/life-rewriter-abstract-v3.png",
  "关系疗愈者": "https://raw.githubusercontent.com/Shelro/WereadPersonalityTest/main/images/relationship-healer-abstract-v3.png",
  "他心翻译者": "https://raw.githubusercontent.com/Shelro/WereadPersonalityTest/main/images/other-mind-translator-abstract-v3.png",
  "人性观察员": "https://raw.githubusercontent.com/Shelro/WereadPersonalityTest/main/images/human-nature-observer-abstract-v3.png",
  "边界修复者": "https://raw.githubusercontent.com/Shelro/WereadPersonalityTest/main/images/boundary-repairer-abstract-v3.png",
  "时代安放者": "https://raw.githubusercontent.com/Shelro/WereadPersonalityTest/main/images/era-placer-abstract-v3.png",
  "弱者看见者": "https://raw.githubusercontent.com/Shelro/WereadPersonalityTest/main/images/vulnerable-witness-abstract-v3.png",
  "制度解剖者": "https://raw.githubusercontent.com/Shelro/WereadPersonalityTest/main/images/system-dissector-abstract-v3.png",
  "现实改良者": "https://raw.githubusercontent.com/Shelro/WereadPersonalityTest/main/images/reality-improver-abstract-v3.png",
  "不确定安放者": "https://raw.githubusercontent.com/Shelro/WereadPersonalityTest/main/images/uncertainty-settler-abstract-v3.png",
  "技术人文守望者": "https://raw.githubusercontent.com/Shelro/WereadPersonalityTest/main/images/tech-humanist-watcher-abstract-v3.png",
  "风险建模师": "https://raw.githubusercontent.com/Shelro/WereadPersonalityTest/main/images/risk-modeler-abstract-v3.png",
  "可能性开拓者": "https://raw.githubusercontent.com/Shelro/WereadPersonalityTest/main/images/possibility-explorer-abstract-v3.png"
}
```

图片处理规则：

1. 如果 URL 是公开直链，可直接在 HTML 中使用。
2. 如果 URL 是分享页而不是图片直链，优先提醒用户改成 GitHub raw、对象存储或 CDN 直链。
3. 不要把网盘账号、密码、Cookie、token 写入 prompt、代码、HTML 或日志。
4. 如果图片暂缺，可以先用 SVG/CSS 占位卡通头像，不影响测试逻辑，并在最终说明里列出缺失的人格名和 URL。
5. HTML 中的 16 型矩阵只给“主型人格 + 3 个副型人格”显示小人图片，其余人格仍以文字卡片展示，以突出主副型差异。
6. 放图片的主型/副型格子不要堆叠长段文字；长期问题、盲区、阅读习惯、困惑与解决路径应放在矩阵前面的主型/副型分析卡片里。

## 八、交付文件

请生成以下文件：

1. `reading-personality-data.json`
   - 包含主型、副型、16 型总览、评分、证据、阅读偏好、长期问题、困惑路径、价值观、建议。

2. `reading-personality.md`
   - 可阅读的文字报告。

3. `reading-personality.html`
   - 可直接打开的可视化页面。

4. 如果使用图片：
   - 本地图片放入 `assets/personas/`
   - 或在 HTML 中引用公开图片 URL。

## 九、验证要求

完成后请验证：

1. 微信读书数据来自最新拉取，而不是旧报告臆测。
2. `reading-personality-data.json` 中：
   - 主型存在且只有 1 个。
   - 副型正好 3 个。
   - `typeCatalog` 正好 16 个。
3. `reading-personality.html` 中：
   - 有 4 个横轴标签。
   - 有 4 个纵轴标签。
   - 有 16 个人格格子。
   - 有 4 种颜色图例。
   - 主型和副型有高亮。
4. 不输出或泄露任何账号密码、API Key、Cookie、token。

## 十、输出语气

请用清晰、克制、有证据感的中文写作。不要把读书人格说成固定性格或命运。可以给出假设，但要标明证据强弱。
