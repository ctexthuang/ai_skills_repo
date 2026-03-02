# Hyperf 3.1 & PostgreSQL 18.3 AI Skill (Expert)

## 📌 Introduction / 简介

This Skill is a highly detailed engineering guideline designed for **Claude Code** and other AI assistants. It ensures the AI adheres to the specific architectural patterns of the `Geeco_server` project, including **Hyperf 3.1**, **PostgreSQL 18**, and a custom **Repository/Service** layer.

这份 Skill 是为 **Claude Code** 及其他 AI 助手设计的深度工程指南。它确保 AI 严格遵守 `Geeco_server` 项目的特定架构模式，包括 **Hyperf 3.1**、**PostgreSQL 18** 以及自定义的 **Repository/Service** 分层架构。(配合 ctexthuang 自研框架)

---

## 🚀 How to Install / 如何安装

According to the [Claude Code Skills Documentation](https://code.claude.com/docs/zh-CN/skills), you should place the `SKILL.md` in a subdirectory of `.claude_code/skills/`.

根据 [Claude Code Skills 官方文档](https://code.claude.com/docs/zh-CN/skills)，你需要将 `SKILL.md` 放入 `.claude_code/skills/` 的子目录中。

### 1. Manual Creation / 手动创建

```bash
mkdir -p .claude_code/skills/hyperf-expert
# Copy the SKILL.md content into this folder
# 将 SKILL.md 内容复制到该文件夹中

```

### 2. Verification / 验证

Start Claude Code and ask:
启动 Claude Code 并提问：

> "What are the core architectural rules for this project?"
> "这个项目的核心架构规则是什么？"

---

## 🎯 Key Features / 核心特性

* 
**Singleton Safety / 单例安全**: Explicitly prevents the AI from storing request state in Service properties, avoiding fatal coroutine context leakage.


* 
**单例安全**: 显式禁止 AI 在 Service 属性中存储请求状态，避免致命的协程上下文泄露 。




* 
**PG18 Optimization / PG18 优化**: Guides the AI to use `JSONB`, `timestamptz`, and advanced indexing features of PostgreSQL 18.3.


* 
**PG18 优化**: 引导 AI 使用 PostgreSQL 18.3 的 `JSONB`、`timestamptz` 及高级索引特性 。




* **Layered Enforcement / 强制分层**: Strictly enforces `Controller -> Service -> Repository -> Model` flow to keep the codebase clean.
* **强制分层**: 严格执行 `控制器 -> 服务 -> 仓库 -> 模型` 流程，保持代码库整洁。


* **Utility Integration / 工具集成**: Pre-defines usage for custom `Logger`, `RedisCache`, and `ResponseFormat` attributes.
* **工具集成**: 预定义了自定义 `Logger`、`RedisCache` 和 `ResponseFormat` 注解的使用方法。



---

## File Structure / 文件结构

```text
.claude_code/
└── skills/
    └── hyperf-expert/
        ├── SKILL.md      # The core expert instructions / 核心专家指令
        └── README.md     # This documentation / 本文档

```

---

##  Warning / 警告

**Do not modify the Singleton Trap section.** This is the most common cause of bugs in Hyperf asynchronous programming. The AI must always use `Context::get()` or the magic `__get` method for request-specific data.

**切勿修改“单例陷阱（Singleton Trap）”部分。** 这是 Hyperf 异步编程中最常见的 Bug 来源。AI 必须始终使用 `Context::get()` 或魔术方法 `__get` 来获取请求相关的数据。

