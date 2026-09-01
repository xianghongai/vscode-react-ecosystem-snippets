# React Stack Snippets (Visual Studio Code)

Everyday React ecosystem code patterns for VS Code: client state, validation, forms, server state, i18n, general hooks, error boundaries, class names and tests.

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

[中文文档](./README_CN.md)

## Design

**One capability per snippet, one scope per language.** All snippets ship in a single `.code-snippets` file. Which languages a snippet reaches is decided by its own `scope` field, not by the file it lives in, so a JavaScript variant and its TypeScript counterpart stay separate definitions and neither leaks into the other's language mode.

**Sources are split by module.** Each library owns a directory under `src/`, and `src/recipes/` owns the cross-library examples. The build merges them in sorted order into the single contributed file. A snippet is identified by its name, so a repeated name fails the build — the later definition would otherwise silently replace the earlier one.

**Prefixes are the discovery path, and they may repeat.** A snippet that wraps one API uses that API's real name (`useForm`, `useQuery`, `queryOptions`, `produce`, `clsx`); a scenario uses a module stem (`rhfSetError`, `queryPagination`, `zustandPersist`, `i18nInit`). Because VS Code triggers on prefix but identifies a snippet by name, several snippets may share a prefix and are offered side by side, labelled by name. Nothing here needs to avoid the prefixes of other snippet extensions you have installed.

**Imports are separate from fragments.** A fragment inserts only the code it is about and names its required imports in its description; a complete file template carries its own imports. Editable placeholders cover what you actually rename — component, hook, type, service function, cache key — while illustrative field names stay literal so the Tab sequence stays short. Repeated identifiers are mirrors and update together.

**Responsibilities stay separate.** TanStack Query owns server state, React Hook Form owns form state, Zod validates data crossing a boundary, and nuqs owns state that lives in the URL. Cross-library recipes compose these without blurring them.

**Where the ecosystem offers alternatives, all of them ship.** Client state has Zustand and Jotai; general hooks have ahooks, react-use, usehooks-ts and rooks. You pick one, so the extension gives each its own snippets using that library's real signature rather than choosing for you. Type the hook name you already know — `useDebounce`, `useCounter`, `useLocalStorage` — and the candidates appear side by side, each labelled with its library.

**This matters most where the same name means different things.** `useDebounce` debounces a value in ahooks but an effect in react-use; `useBoolean` returns a tuple in ahooks and an object in usehooks-ts; `useClickAway` takes its arguments in the opposite order in ahooks and react-use; `useThrottleFn` returns a runner in ahooks and the throttled result in react-use. Picking the wrong one is not a syntax error — it fails at runtime. Each description states which library it is for and calls out the difference.

**No runtime.** The extension contributes snippets and nothing else — no extension-host code, no activation events, no dependency installation, no project detection, no telemetry. Snippets are offered by language mode, never gated on which libraries your project happens to have installed.

## Usage

Install the VSIX through **Extensions → Install from VSIX…**, then open a file in a JavaScript, JavaScript React, TypeScript or TypeScript React language mode.

Type an API name or a module stem and pick from the completion list, or use **Insert Snippet** to browse. Press **Tab** to move through the editing points; the final cursor lands where you continue writing. Enable `editor.tabCompletion` in your settings if you prefer expanding a prefix directly with Tab.

Complete file templates are also reachable through **Snippets: Fill File with Snippet**.

Two conventions are worth knowing:

- **`./service` is the integration boundary.** File recipes import their request functions from a relative `./service` module. Create it with your own request layer, or edit the path and the exported name — both are editable placeholders. No HTTP client, API host, path alias or UI library is prescribed.
- **Pick one i18n type augmentation.** `i18nResourceTypesTS` gives typed string keys; `i18nSelectorTypesTS` enables selector syntax for `i18nTSelector`. They conflict, so a TypeScript project uses one or the other. Selector mode is a type augmentation, not an `init` option.

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

## References

- [VS Code snippet format and scopes](https://code.visualstudio.com/docs/editing/userdefinedsnippets)
- [Immer update patterns](https://immerjs.github.io/immer/update-patterns/)
- [Zustand TypeScript guide](https://zustand.docs.pmnd.rs/learn/guides/advanced-typescript)
- [Zod basics](https://zod.dev/basics)
- [React Hook Form resolver types](https://github.com/react-hook-form/resolvers#typescript)
- [TanStack Query v5](https://tanstack.com/query/v5/docs/framework/react/overview)
- [react-i18next useTranslation](https://react.i18next.com/latest/usetranslation-hook)
- [React Testing Library](https://testing-library.com/docs/react-testing-library/intro/)

MIT licensed. See LICENSE.
