# React Ecosystem Snippets (Visual Studio Code)

VS Code 中的 React 生态日常代码片段：客户端状态、不可变更新、数据校验、表单、服务端状态、URL 状态、国际化、错误边界、类名处理、通用 Hooks 与测试。

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

## 前缀清单

前缀遵循三种模式：

1. **API 名本身就是前缀** —— `useQuery`、`useForm`、`useAtom`、`atom`。库 API 的名字**就是**最终要写下的代码，中间没有翻译环节，无需先记一套映射。
2. **少数日常 API 另配短码** —— `uq` = `useQuery`、`uf` = `useForm`、`ua` = `useAtom`。两种形式挂在同一条片段上，短码是用熟之后的提速手段，而不是上手门槛。通用 Hooks 库一律不配：`useCounter` 有四个库都定义，单一缩写说不清指哪个。
3. **同库共用词干，场景在其后扩展** —— `zustand…`、`zod…`、`rhf…`、`query…`、`i18n…`、`immer…`、`rtl…`。打出词干就能在补全列表里摊开整个库。

### 客户端状态 — Zustand

| 前缀                    | 缩写 | 插入内容                                  |
| ----------------------- | ---- | ----------------------------------------- |
| `zustandAction`         |      | 在 React 组件中选择一个 action            |
| `zustandDevtools`       |      | 为 store 接入 Redux DevTools              |
| `zustandImportCreate`   |      | 导入 Zustand 的 create                    |
| `zustandImportDevtools` |      | 导入 devtools 中间件                      |
| `zustandImportPersist`  |      | 导入 persist 中间件                       |
| `zustandImportShallow`  |      | 导入 useShallow selector 辅助函数         |
| `zustandPersist`        |      | 使用 partialize 持久化 store 中选定的子集 |
| `zustandReset`          |      | 为 state creator 添加 reset action        |
| `zustandSelect`         |      | 在 React 组件中选择一个状态字段           |
| `zustandStore`          | `zs` | 完整的类型化计数器 store 文件             |
| `zustandUseShallow`     |      | 通过一个浅比较 selector 选择多个值        |

### 客户端状态 — Jotai

| 前缀              | 缩写  | 插入内容                                                              |
| ----------------- | ----- | --------------------------------------------------------------------- |
| `atom`            |       | 创建持有单个值的原子                                                  |
| `atomFamily`      |       | 按参数创建一族原子                                                    |
| `atomWithStorage` |       | 创建持久化到 localStorage 的原子                                      |
| `jotaiProvider`   |       | 把原子作用域绑定到显式 store，而非隐式全局 store                      |
| `loadable`        |       | 包裹异步原子，使其返回 loading / hasData / hasError 而不触发 Suspense |
| `selectAtom`      |       | 只订阅较大原子中的一个切片，仅该切片变化时才重渲染                    |
| `splitAtom`       |       | 把列表原子拆成逐项的原子，使单行重渲染不牵动整个列表                  |
| `useAtom`         | `ua`  | 读写原子，并让该组件订阅其值                                          |
| `useAtomValue`    | `uav` | 只读取原子，不获取 setter                                             |
| `useSetAtom`      | `usa` | 只取原子的 setter 而不订阅其值，写入不会触发该组件重渲染              |

### 不可变更新

| 前缀                 | 缩写 | 插入内容                                 |
| -------------------- | ---- | ---------------------------------------- |
| `immerArrayDelete`   |      | 按索引删除 Immer draft 数组元素          |
| `immerArrayInsert`   |      | 向 Immer draft 数组插入元素              |
| `immerArrayUpdate`   |      | 更新 Immer draft 数组元素的属性          |
| `immerCurried`       |      | 创建可复用的柯里化 Immer producer        |
| `immerImportProduce` |      | 导入 Immer 的 produce                    |
| `immerNested`        |      | 在 Immer draft 中安全更新嵌套值          |
| `immerProduce`       | `ip` | 使用 produce 创建不可变的新状态          |
| `immerProduceTs`     |      | 使用 produce 创建类型化的不可变状态副本  |
| `immerReactUpdate`   |      | 通过 React 函数式 setter 应用 Immer 更新 |

### 数据校验

| 前缀                    | 缩写 | 插入内容                                       |
| ----------------------- | ---- | ---------------------------------------------- |
| `zodArray`              |      | 定义 Zod 数组 schema                           |
| `zodCoerceNumber`       |      | 强制转换并校验数值字段，适用于表单与查询串输入 |
| `zodDiscriminatedUnion` |      | 定义以字面量字段为判别键的 Zod 联合类型        |
| `zodEnum`               |      | 定义 Zod 字符串枚举 schema                     |
| `zodImport`             |      | 导入 Zod schema builder                        |
| `zodInputOutput`        |      | 推导带转换的 schema 的输入与输出类型           |
| `zodObject`             | `zo` | 定义 Zod 对象 schema                           |
| `zodOptional`           |      | 向 Zod 对象 shape 添加可选字段                 |
| `zodParseAsync`         |      | 解析带异步 refinement 的数据                   |
| `zodSafeParse`          |      | 在不抛异常的前提下校验未知数据                 |
| `zodTransform`          |      | 定义会转换解析结果的文本 schema                |

### 表单

| 前缀                   | 缩写  | 插入内容                                       |
| ---------------------- | ----- | ---------------------------------------------- |
| `rhfController`        |       | 通过 Controller 绑定非原生或被包装的输入控件   |
| `rhfFormContextField`  |       | 读取上层 FormProvider，避免逐层传递 props      |
| `rhfFormProvider`      |       | 将同一个表单实例共享给嵌套字段组件             |
| `rhfImport`            |       | 导入 React Hook Form 7 API                     |
| `rhfImportZodResolver` |       | 导入 Zod resolver                              |
| `rhfReset`             |       | 数据返回后回填表单，并忽略卸载后才到达的响应   |
| `rhfSetError`          |       | 将提交失败同时映射到对应字段和表单级 root 错误 |
| `useFieldArray`        | `ufa` | 渲染带稳定 key 的可重复字段组                  |
| `useForm`              | `uf`  | 注册原生字段并展示校验信息                     |
| `useWatch`             | `uw`  | 订阅选定字段，使重渲染局限在该子树             |

### 服务端状态

| 前缀               | 缩写  | 插入内容                                                               |
| ------------------ | ----- | ---------------------------------------------------------------------- |
| `queryAbortSignal` |       | 将查询的 AbortSignal 传给请求函数，使被取代的请求得以取消              |
| `queryDependent`   |       | 在输入就绪前挂起查询，避免以 undefined 作为键发起请求                  |
| `queryImport`      |       | 导入 TanStack Query 5 API                                              |
| `queryOptimistic`  |       | 创建乐观更新 mutation，其回滚会区分「onMutate 未完成」与「原本无缓存」 |
| `queryOptions`     | `qo`  | 创建单个资源可复用的 queryOptions                                      |
| `queryPagination`  |       | 分页时保留上一页内容，避免请求期间闪烁                                 |
| `queryPrefetch`    |       | 在悬停与聚焦时预热缓存，使下一次导航立即渲染                           |
| `queryProvider`    |       | 创建稳定的 QueryClient Provider                                        |
| `useInfiniteQuery` | `uiq` | 分页加载无限列表，含 TanStack Query 5 必需的 initialPageParam          |
| `useMutation`      | `um`  | 创建成功后失效缓存键的 mutation                                        |
| `useQuery`         | `uq`  | 渲染查询及其等待与错误状态                                             |

### URL 状态

| 前缀                   | 缩写 | 插入内容                                                   |
| ---------------------- | ---- | ---------------------------------------------------------- |
| `nuqsAdapter`          |      | 提供 nuqs 2 必需的适配器，需置于所有使用其 Hook 的组件之上 |
| `parseAsArrayOf`       |      | 把带分隔符的查询参数解析为数组                             |
| `parseAsStringLiteral` |      | 把查询参数限定在固定的字符串集合内，其余取值一律拒绝       |
| `useQueryState`        |      | 将一个字符串状态与 URL 查询参数同步，参数不存在时值为 null |
| `useQueryStates`       |      | 把多个 URL 查询参数作为一个对象读写，并合并为单条历史记录  |

### 国际化

| 前缀                          | 缩写 | 插入内容                                                                     |
| ----------------------------- | ---- | ---------------------------------------------------------------------------- |
| `i18nChangeLanguage`          |      | 切换当前语言                                                                 |
| `i18nImportTrans`             |      | 从 react-i18next 导入 Trans，用于组件插值                                    |
| `i18nImportTranslation`       |      | 从 react-i18next 导入 Translation，用于 render prop 形式                     |
| `i18nImportUseTranslation`    |      | 从 react-i18next 导入 useTranslation                                         |
| `i18nInitJS`                  |      | i18next 26 + react-i18next 17 的本地资源完整初始化                           |
| `i18nInitTS`                  |      | i18next 26 + react-i18next 17 的本地资源完整初始化                           |
| `i18nResourceTypesTS`         |      | 本地 i18n 模块的 TypeScript 资源类型增强                                     |
| `i18nSelectorTypesTS`         |      | i18next 26.4+ 的 TypeScript selector 模式增强                                |
| `i18nTSelector`               |      | 使用 i18next selector 语法翻译                                               |
| `i18nTrans`                   |      | 渲染带变量和嵌套 React 内容的 react-i18next Trans 组件                       |
| `i18nTranslateInterpolation`  |      | 使用插值变量翻译 key                                                         |
| `i18nTranslateNamespace`      |      | 为单次调用指定其他命名空间，不改变 useTranslation 已绑定的命名空间           |
| `i18nTranslatePlural`         |      | 使用 count 翻译 i18next 复数 key                                             |
| `i18nTranslationRenderProp`   |      | 通过 render prop 向子节点提供 t，适用于无法使用 Hook 的场合，例如 class 组件 |
| `i18nUseTranslationNamespace` |      | 获取一个命名空间的 t 和 i18n 实例                                            |

### 错误边界

| 前缀                             | 缩写 | 插入内容                                                   |
| -------------------------------- | ---- | ---------------------------------------------------------- |
| `reactErrorBoundaryAsync`        |      | 将异步事件处理器失败交给最近的错误边界                     |
| `reactErrorBoundaryComponentJSX` |      | 带无障碍降级 UI 和重置操作的完整 JavaScript React 错误边界 |
| `reactErrorBoundaryComponentTSX` |      | 带无障碍降级 UI 和重置操作的完整 TypeScript React 错误边界 |
| `reactErrorBoundaryFallbackJS`   |      | 创建 ErrorBoundary 的 fallbackRender 回调                  |
| `reactErrorBoundaryFallbackTS`   |      | 创建带类型的 ErrorBoundary fallbackRender 回调             |
| `reactErrorBoundaryImport`       |      | 从 react-error-boundary 6 导入 ErrorBoundary               |
| `reactErrorBoundaryResetKeys`    |      | 创建 ErrorBoundary 的重置选项                              |

### 类名处理

| 前缀              | 缩写 | 插入内容                                           |
| ----------------- | ---- | -------------------------------------------------- |
| `clsxConditional` |      | 组合条件 className                                 |
| `clsxImport`      |      | 导入 clsx 2 以组合条件 className                   |
| `cnUtilityJS`     |      | 完整的 JavaScript cn 工具                          |
| `cnUtilityTS`     |      | 完整的 TypeScript cn 工具                          |
| `twMergeClasses`  |      | 合并 Tailwind 工具类并保留冲突中的最终值           |
| `twMergeImport`   |      | 导入 tailwind-merge 3 以解决冲突的 Tailwind 工具类 |

### 通用 Hooks

| 前缀                   | ahooks | react-use | usehooks-ts | rooks |
| ---------------------- | ------ | --------- | ----------- | ----- |
| `useBoolean`           | ●      |           | ●           |       |
| `useClickAway`         | ●      | ●         |             |       |
| `useCopyToClipboard`   |        | ●         | ●           |       |
| `useCounter`           | ●      | ●         | ●           | ●     |
| `useDebounce`          | ●      | ●         |             |       |
| `useDebounceCallback`  |        |           | ●           |       |
| `useDebounceFn`        | ●      |           |             | ●     |
| `useDebounceValue`     |        |           | ●           |       |
| `useDebouncedValue`    |        |           |             | ●     |
| `useEvent`             |        | ●         |             |       |
| `useEventListener`     | ●      |           | ●           |       |
| `useFreshCallback`     |        |           |             | ●     |
| `useInterval`          | ●      | ●         | ●           |       |
| `useIntervalWhen`      |        |           |             | ●     |
| `useKey`               |        |           |             | ●     |
| `useLocalStorage`      |        | ●         | ●           |       |
| `useLocalStorageState` | ●      |           |             |       |
| `useLocalstorageState` |        |           |             | ●     |
| `useMedia`             |        | ●         |             |       |
| `useMediaMatch`        |        |           |             | ●     |
| `useMediaQuery`        |        |           | ●           |       |
| `useMemoizedFn`        | ●      |           |             |       |
| `useOnClickOutside`    |        |           | ●           |       |
| `useOutsideClickRef`   |        |           |             | ●     |
| `useThrottle`          | ●      | ●         |             | ●     |
| `useThrottleFn`        | ●      | ●         |             |       |
| `useToggle`            |        | ●         | ●           | ●     |

### 测试

| 前缀                         | 缩写 | 插入内容                                                                       |
| ---------------------------- | ---- | ------------------------------------------------------------------------------ |
| `rtlAsyncUiJSX`              |      | 面向 Vitest 4、RTL 16 和 user-event 14 的完整异步 UI 测试                      |
| `rtlAsyncUiTSX`              |      | 面向 Vitest 4、RTL 16 和 user-event 14 的完整 TypeScript 异步 UI 测试          |
| `rtlComponentInteractionJSX` |      | 完整的 Vitest 4 + React Testing Library 16 + user-event 14 交互测试            |
| `rtlComponentInteractionTSX` |      | 完整的 TypeScript Vitest 4 + React Testing Library 16 + user-event 14 交互测试 |
| `rtlQueryWrapperJSX`         |      | 为 RTL 测试创建隔离的 TanStack Query 5 wrapper                                 |
| `rtlQueryWrapperTSX`         |      | 为 RTL 测试创建隔离的 TypeScript TanStack Query 5 wrapper                      |
| `rtlRenderHookJS`            |      | 使用 RTL 16 renderHook 和 Vitest 4 的完整 Hook 交互测试                        |
| `rtlRenderHookTS`            |      | 使用 RTL 16 renderHook 和 Vitest 4 的完整 TypeScript Hook 交互测试             |
| `testStoreResetJS`           |      | 每个用例前重置测试 store                                                       |
| `testStoreResetTS`           |      | 每个用例前重置带类型的测试 store                                               |

### 组合场景

| 前缀                 | 缩写 | 插入内容                                                                      |
| -------------------- | ---- | ----------------------------------------------------------------------------- |
| `reactFormMutation`  |      | 完整的提交链路：校验、将提交失败映射为 root 错误、失效列表缓存并重置          |
| `reactQueryBoundary` |      | 将查询失败抛给错误边界，并由 QueryErrorResetBoundary 驱动重试                 |
| `reactQueryZod`      |      | 在查询边界校验服务响应，使非法数据不会进入组件                                |
| `reactSearchQuery`   |      | 防抖搜索：缓存键使用防抖后的关键词，请求接收查询的 AbortSignal                |
| `rhfZodForm`         |      | 由单个 Zod schema 校验的完整表单文件                                          |
| `zustandImmer`       |      | 按正确顺序组合 Immer draft、persist partialize 与 devtools 的完整类型化 store |

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
