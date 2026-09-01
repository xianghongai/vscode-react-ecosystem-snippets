# React Stack Snippets (Visual Studio Code)

VS Code 中的 React 生态日常代码片段：客户端状态、数据校验、表单、服务端状态、国际化、通用 Hooks、错误边界、类名与测试。

<p>
  <a href="https://github.com/xianghongai/vscode-react-ecosystem-snippets">
    <img src="https://img.shields.io/github/repo-size/xianghongai/vscode-react-ecosystem-snippets?color=4ac51c&style=plastic" alt="Repo Size">
  </a>
  <a href="https://marketplace.visualstudio.com/items?itemName=nicholashsiang.vscode-react-ecosystem-snippets">
    <img src="https://vsmarketplacebadges.dev/version/nicholashsiang.vscode-react-ecosystem-snippets.svg?style=plastic&color=4ac51c" alt="Visual Studio Marketplace Version">
  </a>
  <a href="https://marketplace.visualstudio.com/items?itemName=nicholashsiang.vscode-react-ecosystem-snippets">
    <img src="https://vsmarketplacebadges.dev/downloads-short/nicholashsiang.vscode-react-ecosystem-snippets.svg?style=plastic&color=4ac51c" alt="Downloads">
  </a>
  <a href="https://marketplace.visualstudio.com/items?itemName=nicholashsiang.vscode-react-ecosystem-snippets">
    <img src="https://vsmarketplacebadges.dev/rating-short/nicholashsiang.vscode-react-ecosystem-snippets.svg?style=plastic&color=4ac51c" alt="Rating">
  </a>
  <a href="https://github.com/xianghongai/vscode-react-ecosystem-snippets/blob/HEAD/LICENSE">
    <img src="https://img.shields.io/github/license/xianghongai/vscode-react-ecosystem-snippets?color=4ac51c&style=plastic" alt="License">
  </a>
</p>

[English](./README.md)

## 设计

**一条片段一个能力，一个 scope 决定投放语言。** 所有片段合并在单个 `.code-snippets` 文件中。某条片段出现在哪些语言，由它自己的 `scope` 字段决定，与它落在哪个文件无关——因此 JavaScript 变体与其 TypeScript 对应版本是两条独立定义，互不串到对方的语言模式里。

**片段源按模块拆分。** 每个库在 `src/` 下拥有一个目录，跨库组合场景归 `src/recipes/`。构建按排序合并成唯一的贡献文件。片段以名称标识，因此名称重复会导致构建失败——否则后者会静默覆盖前者。

**前缀是主要发现入口，且允许重复。** 封装单个 API 的片段直接用该 API 的真名（`useForm`、`useQuery`、`queryOptions`、`produce`、`clsx`）；场景类使用模块词干（`rhfSetError`、`queryPagination`、`zustandPersist`、`i18nInit`）。VS Code 靠前缀触发、靠名称识别片段，因此多条片段可以共用一个前缀，会并列出现在候选中并以名称区分。这里无需回避其他已安装片段扩展所使用的前缀。

**导入与片段正文分离。** 碎片类片段只插入它本身相关的代码，所需导入写在描述里；完整文件模板自带 imports。可编辑占位符覆盖真正需要改名的部分——组件、Hook、类型、服务函数、缓存键——示例字段名保持字面量，以免 Tab 序列过长。重复出现的标识符是镜像，会联动更新。

**职责边界保持独立。** TanStack Query 管服务端状态，React Hook Form 管表单状态，Zod 校验跨边界的数据，nuqs 管存在 URL 里的状态。跨库组合场景只做组合，不模糊这些边界。

**生态里存在多个同类选择时，一并提供。** 客户端状态有 Zustand 与 Jotai，通用 Hooks 有 ahooks、react-use、usehooks-ts 与 rooks。选哪个是使用方的决定，因此扩展按各库**真实签名**分别提供片段，而不替其做选择。直接敲已经记得的那个 Hook 名——`useDebounce`、`useCounter`、`useLocalStorage`——候选会并列出现，各自标注所属库。

**同名反义之处尤其需要这样处理。** `useDebounce` 在 ahooks 防抖的是值、在 react-use 防抖的是副作用；`useBoolean` 在 ahooks 返回数组、在 usehooks-ts 返回对象；`useClickAway` 在 ahooks 与 react-use 之间参数顺序相反；`useThrottleFn` 在 ahooks 返回运行器、在 react-use 返回节流后的结果。选错不会报语法错，只在运行时失败。每条描述都写明所属库并点出差异。

**没有运行时。** 该扩展只贡献片段：没有扩展宿主代码、没有激活事件、不安装依赖、不探测项目、不采集数据。片段按语言模式提供候选，不会因项目是否安装某个库而自动启停。

## 使用

通过 **Extensions → Install from VSIX…** 安装，然后在 JavaScript、JavaScript React、TypeScript 或 TypeScript React 语言模式下打开文件。

输入 API 名或模块词干，从补全列表中选择，也可通过 **Insert Snippet** 浏览。按 **Tab** 在编辑点之间移动，最终光标停在继续书写的位置。若希望直接按前缀 Tab 展开，可在个人设置中开启 `editor.tabCompletion`。

完整文件模板也可通过 **Snippets: Fill File with Snippet** 插入。

有两处约定需要知晓：

- **`./service` 是应用接入点。** 完整场景片段从相对路径 `./service` 导入请求函数。请用自身的请求层实现该模块，或直接修改路径与导出名——两者都是可编辑占位符。示例不约定 HTTP 客户端、API 域名、路径别名或 UI 组件库。
- **国际化类型增强二选一。** `i18nResourceTypesTS` 提供带资源推导的字符串键；`i18nSelectorTypesTS` 启用 selector 语法，供 `i18nTSelector` 使用。两者冲突，同一个 TypeScript 工程只能选其一。selector 属于类型增强，不是 `init` 的运行时参数。

## 模块

扩展本身不依赖下列库，在应用中按需安装即可。版本为已验证的大版本组合，并不宣称覆盖全部历史小版本。

| 模块       | 安装                                                                                                     |
| ---------- | -------------------------------------------------------------------------------------------------------- |
| 不可变更新 | `immer@11`                                                                                               |
| 客户端状态 | `zustand@5` 或 `jotai@2`（Zustand + Immer 组合场景还需 `immer@11`）                                      |
| URL 状态   | `nuqs@2`，以及与所用路由匹配的 adapter                                                                   |
| 数据校验   | `zod@4`                                                                                                  |
| 表单       | `react-hook-form@7 @hookform/resolvers@5 zod@4`                                                          |
| 服务端状态 | `@tanstack/react-query@5`                                                                                |
| 通用 Hooks | `ahooks@3`、`react-use@17`、`usehooks-ts@3` 或 `rooks@9`                                                 |
| 国际化     | `i18next@26 react-i18next@17`                                                                            |
| 错误边界   | `react-error-boundary@6`                                                                                 |
| 类名处理   | `clsx@2`，Tailwind CSS 4 项目另需 `tailwind-merge@3`                                                     |
| 测试       | `vitest@4 jsdom@30 @testing-library/react@16 @testing-library/user-event@14 @testing-library/jest-dom@6` |

验证目标为 React 19。TypeScript 工程还需匹配的 React 类型包。测试片段假定存在 DOM 测试环境、自动 JSX runtime 与 jest-dom setup，它们本身不负责初始化测试框架。

给出多个选项的行是**互斥的备选**，不是要一起装——通常只选一个客户端状态库和一个通用 Hooks 库。nuqs 2 另需在使用其 Hook 的组件之上挂载 adapter；`nuqsAdapter` 片段完成该配置，并在描述中给出其他路由对应的 adapter 路径。

从源码自建，环境变量 `SNIPPETS_EXCLUDE` 可调整目录排除来源，如，设为 `src/ahooks/**,src/react-use/**` 即只打包 `usehooks-ts` 的片段。写进已被 git 忽略的 `.env`，该选择便不进入源码树；命令行传入的值优先于该文件。

## 官方依据

- [VS Code 片段格式与 scope](https://code.visualstudio.com/docs/editing/userdefinedsnippets)
- [Immer 更新模式](https://immerjs.github.io/immer/update-patterns/)
- [Zustand TypeScript 指南](https://zustand.docs.pmnd.rs/learn/guides/advanced-typescript)
- [Zod 基础](https://zod.dev/basics)
- [React Hook Form resolver 类型](https://github.com/react-hook-form/resolvers#typescript)
- [TanStack Query v5](https://tanstack.com/query/v5/docs/framework/react/overview)
- [react-i18next useTranslation](https://react.i18next.com/latest/usetranslation-hook)
- [React Testing Library](https://testing-library.com/docs/react-testing-library/intro/)

MIT 许可，见 LICENSE。
