# JetBrains Rider Theme for Zed

[English](#english) | [中文](#中文)

## English

Two themes, **JetBrains Rider Islands Light** and **JetBrains Rider Islands Dark**, whose editor and syntax colors were taken from the
default *Rider Light* and *Rider Dark* color schemes (Rider 2026.2).

Features:

- Editor colors: background, gutter, caret row, selection, line numbers, indent guides, highlighted identifier, search match, matched brace, diff and diagnostic colors.
- Tree-sitter syntax colors for all languages (keyword, string, number, comment, type, function, property, ...).
- Extra named styles under the `rider.*` prefix (`rider.class`, `rider.struct`, `rider.interface`, `rider.enum`, `rider.delegate`,
  `rider.type_parameter`, `rider.namespace`, `rider.field`, `rider.property`, `rider.constant`, `rider.enum_member`,
  `rider.event`, `rider.method`, `rider.extension_method`, `rider.local`, `rider.parameter`, ...) for LSP semantic tokens.

### Recommended C# setup

Themes cannot ship settings, so copy this into your `settings.json`. It turns on `semantic_tokens: "combined"` and maps C# semantic tokens
to the theme styles (rules fall back to standard styles when another theme is active).
The rules work with both Zed's default **Roslyn** language server and [csharp-ls](https://github.com/razzmatazz/csharp-language-server).
The `language_servers` line selects csharp-ls (lighter on memory); remove it to keep the default Roslyn.

```json
{
  "languages": {
    "CSharp": {
      "language_servers": [
        "csharp-ls",
        "!roslyn",
        "!omnisharp",
        "..."
      ],
      "semantic_tokens": "combined"
    }
  },
  "global_lsp_settings": {
    "semantic_token_rules": [
      {
        "token_type": "class",
        "style": [
          "rider.class",
          "type.class",
          "type"
        ]
      },
      {
        "token_type": "struct",
        "style": [
          "rider.struct",
          "type"
        ]
      },
      {
        "token_type": "interface",
        "style": [
          "rider.interface",
          "type.interface",
          "type"
        ]
      },
      {
        "token_type": "enum",
        "style": [
          "rider.enum",
          "enum",
          "type"
        ]
      },
      {
        "token_type": "typeParameter",
        "style": [
          "rider.type_parameter",
          "type"
        ]
      },
      {
        "token_type": "namespace",
        "style": [
          "rider.namespace",
          "namespace"
        ]
      },
      {
        "token_type": "field",
        "style": [
          "rider.field",
          "property"
        ]
      },
      {
        "token_type": "property",
        "style": [
          "rider.property",
          "property"
        ]
      },
      {
        "token_type": "constant",
        "style": [
          "rider.constant",
          "constant"
        ]
      },
      {
        "token_type": "enumMember",
        "style": [
          "rider.enum_member",
          "constant"
        ]
      },
      {
        "token_type": "event",
        "style": [
          "rider.event",
          "property"
        ]
      },
      {
        "token_type": "method",
        "style": [
          "rider.method",
          "function"
        ]
      },
      {
        "token_type": "parameter",
        "style": [
          "rider.parameter",
          "variable.parameter",
          "variable"
        ]
      },
      {
        "token_type": "variable",
        "style": [
          "rider.local",
          "variable"
        ]
      },
      {
        "token_type": "keyword",
        "style": [
          "rider.keyword",
          "keyword"
        ]
      },
      {
        "token_type": "string",
        "style": [
          "rider.string",
          "string"
        ]
      },
      {
        "token_type": "stringEscapeCharacter",
        "style": [
          "rider.string_escape",
          "string.escape"
        ]
      },
      {
        "token_type": "number",
        "style": [
          "rider.number",
          "number"
        ]
      },
      {
        "token_type": "comment",
        "style": [
          "rider.comment",
          "comment"
        ]
      },
      {
        "token_type": "operator",
        "style": [
          "rider.operator",
          "operator"
        ]
      },
      {
        "token_type": "delegate",
        "style": ["rider.delegate", "type"]
      },
      {
        "token_type": "extensionMethod",
        "style": ["rider.extension_method", "function"]
      },
      {
        "token_type": "recordClass",
        "style": ["rider.class", "type"]
      },
      {
        "token_type": "recordStruct",
        "style": ["rider.struct", "type"]
      },
      {
        "token_type": "controlKeyword",
        "style": ["rider.keyword", "keyword"]
      },
      {
        "token_type": "stringVerbatim",
        "style": ["rider.string", "string"]
      }
    ]
  },
  "theme": {
    "mode": "system",
    "light": "JetBrains Rider Islands Light",
    "dark": "JetBrains Rider Islands Dark"
  }
}
```

Then run `editor: restart language server`. Use `dev: open highlights tree view` to inspect tokens.

With Roslyn, delegates, extension methods and records get their own colors. csharp-ls 0.28 reports delegates as `class` and
extension methods as `method`, so there they look like classes / normal methods. Property, enum member and constant colors are
inherited values in Rider's scheme and are approximated with the field/constant colors.

Not affiliated with or endorsed by JetBrains. "Rider" is a trademark of JetBrains s.r.o.; it is used here only to describe the color palette.

## 中文

两个主题：**JetBrains Rider Islands Light** 和 **JetBrains Rider Islands Dark**。编辑器与语法颜色取自 Rider 2026.2 自带的 *Rider Light* / *Rider Dark* 配色方案。

功能：

- 编辑器颜色：背景、行号栏、当前行、选区、行号、缩进线、标识符高亮、搜索匹配、括号匹配、diff 与诊断颜色。
- 所有语言的 Tree-sitter 语法颜色（关键字、字符串、数字、注释、类型、函数、属性等）。
- 额外的 `rider.*` 命名样式（类、结构体、接口、枚举、委托、类型参数、命名空间、字段、属性、常量、枚举成员、事件、方法、扩展方法、局部变量、参数……），供 LSP 语义高亮使用。

### 推荐的 C# 配置

主题无法附带设置，请把上方 JSON 片段复制到 `settings.json`：`semantic_tokens` 设为 `"combined"`，并通过
`global_lsp_settings.semantic_token_rules` 把 token 映射到本主题的样式（切换到其他主题时会回退到通用样式）。
同时支持 Zed 默认的 **Roslyn** 和 csharp-ls。`language_servers` 那一行是切换到更省内存的 csharp-ls，删掉即可继续用 Roslyn。
之后执行 `editor: restart language server`；可用 `dev: open highlights tree view` 查看 token。

使用 Roslyn 时，委托、扩展方法、record 都有单独颜色；csharp-ls 0.28 把委托报成 `class`、扩展方法报成 `method`，所以看起来和类 / 普通方法一样。
属性、枚举成员、常量在 Rider 配色中为继承值，这里用字段 / 常量颜色近似。

本项目与 JetBrains 无关，也未获其认可。“Rider” 是 JetBrains s.r.o. 的商标，此处仅用于描述配色。
