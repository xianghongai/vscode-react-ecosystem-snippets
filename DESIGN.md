# DESIGN

## Modules

The extension carries no runtime dependency on these libraries; install in your application only the ones you use. Versions below are the tested major-version families, not a claim about every historical minor release.

| Module            | Install                                                                                                  |
| ----------------- | -------------------------------------------------------------------------------------------------------- |
| Immutable updates | `immer@11`                                                                                               |
| Client state      | `zustand@5` or `jotai@2` (the Zustand + Immer recipe also needs `immer@11`)                              |
| URL state         | `nuqs@2`, plus the adapter for your router                                                               |
| Validation        | `zod@4`                                                                                                  |
| Forms             | `react-hook-form@7 @hookform/resolvers@5 zod@4`                                                          |
| Server state      | `@tanstack/react-query@5`                                                                                |
| General hooks     | `ahooks@3`, `react-use@17`, `usehooks-ts@3` or `rooks@9`                                                 |
| i18n              | `i18next@26 react-i18next@17`                                                                            |
| Error boundaries  | `react-error-boundary@6`                                                                                 |
| Class names       | `clsx@2`, and `tailwind-merge@3` for Tailwind CSS 4 projects                                             |
| Tests             | `vitest@4 jsdom@30 @testing-library/react@16 @testing-library/user-event@14 @testing-library/jest-dom@6` |

React 19 is the tested target. TypeScript projects also need the matching React type packages. Testing snippets assume a DOM environment, the automatic JSX runtime and a jest-dom setup — they do not initialize a test framework for you.

Rows offering a choice are alternatives, not a set to install together — one client-state library and one general-hooks library is the normal case. nuqs 2 additionally requires mounting an adapter above any component using its hooks; the `nuqsAdapter` snippet sets this up and names the adapter paths for other routers.

When building from source, you can set `SNIPPETS_EXCLUDE` to exclude whole directories from the source. For instance, `SNIPPETS_EXCLUDE=src/ahooks/**,src/react-use/**` bundles only the snippets from `usehooks-ts`. Put it in a gitignored `.env` so the choice stays out of the source tree; a value passed on the command line wins over the file.

---

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

给出多个选项的行是**互斥的备选**，不是要一起装，通常只选一个客户端状态库和一个通用 Hooks 库。nuqs 2 另需在使用其 Hook 的组件之上挂载 adapter；`nuqsAdapter` 片段完成该配置，并在描述中给出其他路由对应的 adapter 路径。

从源码自建，环境变量 `SNIPPETS_EXCLUDE` 可调整目录排除来源，如，设为 `src/ahooks/**,src/react-use/**` 即只打包 `usehooks-ts` 的片段。写进已被 git 忽略的 `.env`，该选择便不进入源码树；命令行传入的值优先于该文件。
