# Weread Personality Test

这是一个用于「微信读书 16 型读书人格测试」的公开资源仓库。

项目目标是让用户可以通过一段可分享的 prompt，调用微信读书 skill 获取自己的最新阅读数据，并生成一份包含主型人格、副型人格、阅读偏好、未来阅读建议和 16 型人格总览的可视化报告。

仓库中的图片资源用于报告里的 16 种读书人格卡通形象。分享 prompt 会通过 GitHub raw 链接直接引用这些图片，因此使用者不需要额外下载或上传图片。

## 文件目录

```text
WereadPersonalityTest/
├── README.md
├── LICENSE
├── personality-assets-github.json
├── reading-personality-share-prompt.md
└── images/
    ├── inner-harbor-abstract-v3.png
    ├── inner-echo-abstract-v3.png
    ├── self-modeler-abstract-v3.png
    ├── life-rewriter-abstract-v3.png
    ├── relationship-healer-abstract-v3.png
    ├── other-mind-translator-abstract-v3.png
    ├── human-nature-observer-abstract-v3.png
    ├── boundary-repairer-abstract-v3.png
    ├── era-placer-abstract-v3.png
    ├── vulnerable-witness-abstract-v3.png
    ├── system-dissector-abstract-v3.png
    ├── reality-improver-abstract-v3.png
    ├── uncertainty-settler-abstract-v3.png
    ├── tech-humanist-watcher-abstract-v3.png
    ├── risk-modeler-abstract-v3.png
    ├── possibility-explorer-abstract-v3.png
    └── green-abstract-v3-sheet.png
```

## 文件说明

- `reading-personality-share-prompt.md`：可直接分享给 Codex / ChatGPT 使用的完整 prompt。
- `personality-assets-github.json`：16 型人格名称到 GitHub raw 图片链接的映射表。
- `images/`：16 张抽象小人图片，以及一张绿色系预览拼图。
- `LICENSE`：仓库许可证。

## 使用方式

1. 打开 `reading-personality-share-prompt.md`。
2. 将 prompt 复制到支持调用微信读书 skill 的环境中。
3. 按 prompt 执行后，会生成：
   - `reading-personality-data.json`
   - `reading-personality.md`
   - `reading-personality.html`

生成的 HTML 报告会自动引用本仓库中的 16 型人格图片。
