![宇航员线稿配图：让动作，讲清一个观点](assets/readme/hero.png)

# 月明·宇航员线稿配图

把一个观点画成宇航员正在做的动作，为文章、画布和视频提供可复用的白底手绘插画。

## 你会得到什么

- 保留绿色 C／月牙面罩的宇航员线稿图
- 围绕当前观点设计的角色动作、道具和少量中文标注
- 图片版本、提示词与素材清单记录

## 试着这样说

```text
用 moonlit-astronaut-illustration。用宇航员线稿解释这段话里的协作关系。画出不同岗位的动作和交接物，先复用我提供的角色参考。
```

## 安装与首次使用

将本仓库的完整目录交给支持本地 Skill 的 Agent 安装，保留 `SKILL.md` 与随附资源。已有同名版本时先检查差异；使用版本锁的工作区沿用自身升级机制。

让 Agent 安装：

```text
请安装这个 Skill：https://github.com/zzyong24/moonlit-astronaut-illustration
```

也可通过 Skills CLI 安装：

```bash
npx skills add zzyong24/moonlit-astronaut-illustration
```

## 配置与依赖

需要支持参考图输入的 image_gen 生图能力，以及已确认的月明角色和风格参考。角色素材由使用方提供或按参考文件解析；安装规则本身不会附送所有历史作品。素材契约随本 Skill 提供。

## 数据与使用边界

参考图片和提示词会交给所选图像生成服务。输出写入作品素材目录；当前规则包含 Moonlit Creator 的素材登记约定。正文组织、整份画布布局和平台发布由其他能力负责。

## 详细说明

执行流程与资源导航见 [SKILL.md](SKILL.md)。安装检查不代表真实业务验收；需要外部服务、账号登录或付费生成的步骤，应在使用者自己的环境中验证。

---

月明水清深 · `moonlit-astronaut-illustration`

首图为 AI 生成的品牌概念插画，不是工具截图或执行结果。
