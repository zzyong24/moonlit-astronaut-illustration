# 共享配图合同

## 输入与输出

配图能力名：`illustration.prepare`（逻辑能力名，不是新增工具命令）。消费者可以是公众号、演示或社交内容 Skill。

输入：work_id、claim（一句话解释任务）、source_anchor（内容章节或稳定段落标识）、labels、roles/actions、style、目标尺寸、existing_asset_id（有则传入）、change_request（仅改图时）。事实证据图必须提供真实素材，不用生图代替。

输出：图片文件、asset_id、revision、sha256、width/height、claim、style、role（explanation/evidence/cover）、prompt_record、reference_paths、review_status、consumers。生成参数与角色质量由配图 Skill 维护，消费者只提供领域需求。

## 文件与状态所有权

- 原图保存在当前作品 `production/illustrations/<组>/<文件>.png`；共享清单为 `production/illustrations/visual-manifest.json`。其中 sourcePath 相对作品根目录。
- 配图 Skill 负责资产内容与版本记录；各形态 Skill 负责本形态的 asset_id/revision 使用清单与布局；主编排更新 work.json 的当前入口。不要让消费者直接改素材版本。
- 清单使用 `schemaVersion`、`brand`、`assets`；每项至少记录上述输出字段。review_status 区分 generated、reviewed、user_approved，已目视检查不等于用户已确认。
- 可重复调用：同一解释任务与参数且已有合适资产时返回现有版本。重画产生新 revision，不覆盖已被引用的旧版；用图像 hash 判定实际文件内容。
- 失败时保留旧资产与旧消费者；仅缺失的新图记为未完成，不用占位图冒充最终图。
- 读回：检查文件存在、像素尺寸、sha256，并查看图内文字、动作与关系。供应商成功不等于内容合格。

## 文章与演示的使用

公众号阶段先产图、嵌图。演示阶段按 claim 和 source_anchor 查找并查看，合适即复用同一文件；不用从文章截图抠图，不用重新生成同义图。

文章发布适配清单 `content/article/assets/visual-manifest.json` 是共享清单的派生视图：顶层 brand、images；每项 path 相对文章目录，并带 type（brand-ai 等）、meaning、ip_markers、asset_id、revision、sha256。保持现有 check_visuals.py 兼容。

Excalidraw 可把同一图片内嵌到文件以保证可搬走使用，同时在 canvas manifest / article-map 记录 asset_id 与 revision。这是交付封装，不是另一张可独立修改的素材原图。

文章措辞变化但图片命题未变，可保留原图；图片意思变化则由配图 Skill 出新版本，主编排列出受影响消费者。已发布包保持原样，更新只进入新的审阅版本。不创建额外素材服务、数据库或逐操作 Skill。
