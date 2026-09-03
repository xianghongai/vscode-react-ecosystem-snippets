# React Ecosystem Snippets (Visual Studio Code)

Everyday React ecosystem patterns for VS Code: client state, immutable updates, validation, forms, server state, URL state, i18n, error boundaries, class names, general hooks and tests.

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

[中文文档](./README.zh-CN.md)

## Prefixes

Prefixes follow three patterns:

1. **The API name is the prefix** — `useQuery`, `useForm`, `useAtom`, `atom`. A library API's name _is_ the code you are about to write, so there is no mapping to memorize first.
2. **A few daily APIs also answer to a short alias** — `uq` = `useQuery`, `uf` = `useForm`, `ua` = `useAtom`. Both forms sit on the same snippet, so the alias is a speed-up once you know it, never the way in. The general-hooks libraries get none: four of them define `useCounter`, so a single alias could not say which.
3. **A library shares a stem, its scenarios extend it** — `zustand…`, `zod…`, `rhf…`, `query…`, `i18n…`, `immer…`, `rtl…`. Type the stem and the completion list lays the whole library out.

### Client state — Zustand

| Prefix                  | Alias | Inserts                                                     |
| ----------------------- | ----- | ----------------------------------------------------------- |
| `zustandAction`         |       | Select one action in a React component                      |
| `zustandDevtools`       |       | Instrument a store with Redux DevTools                      |
| `zustandImportCreate`   |       | Import Zustand create                                       |
| `zustandImportDevtools` |       | Import the devtools middleware                              |
| `zustandImportPersist`  |       | Import the persist middleware                               |
| `zustandImportShallow`  |       | Import the useShallow selector helper                       |
| `zustandPersist`        |       | Persist a chosen subset of the store with partialize        |
| `zustandReset`          |       | Add a reset action to a state creator                       |
| `zustandSelect`         |       | Select one state field in a React component                 |
| `zustandStore`          | `zs`  | Complete typed counter store file                           |
| `zustandUseShallow`     |       | Select several values through one shallow-compared selector |

### Client state — Jotai

| Prefix            | Alias | Inserts                                                                                             |
| ----------------- | ----- | --------------------------------------------------------------------------------------------------- |
| `atom`            |       | Create a primitive atom holding one value                                                           |
| `atomFamily`      |       | Create atoms keyed by a parameter                                                                   |
| `atomWithStorage` |       | Create an atom persisted to localStorage                                                            |
| `jotaiProvider`   |       | Scope atoms to an explicit store instead of the implicit global one                                 |
| `loadable`        |       | Wrap an async atom so it yields loading, hasData or hasError instead of suspending                  |
| `selectAtom`      |       | Subscribe to one slice of a larger atom, re-rendering only when that slice changes                  |
| `splitAtom`       |       | Split a list atom into one atom per item, so a row re-renders without the whole list                |
| `useAtom`         | `ua`  | Read and write an atom, subscribing this component to its value                                     |
| `useAtomValue`    | `uav` | Read an atom without subscribing to a setter                                                        |
| `useSetAtom`      | `usa` | Get an atom's setter without subscribing to its value, so writing does not re-render this component |

### Immutable updates

| Prefix               | Alias | Inserts                                                       |
| -------------------- | ----- | ------------------------------------------------------------- |
| `immerArrayDelete`   |       | Remove an item from an Immer draft array by index             |
| `immerArrayInsert`   |       | Insert an item into an Immer draft array                      |
| `immerArrayUpdate`   |       | Update an item property in an Immer draft array               |
| `immerCurried`       |       | Create a reusable curried Immer producer                      |
| `immerImportProduce` |       | Import Immer produce                                          |
| `immerNested`        |       | Update a nested value safely inside an Immer draft            |
| `immerProduce`       | `ip`  | Create an immutable next state with produce                   |
| `immerProduceTs`     |       | Create a typed immutable state copy with produce              |
| `immerReactUpdate`   |       | Apply an Immer update through a React functional state setter |

### Validation

| Prefix                  | Alias | Inserts                                                              |
| ----------------------- | ----- | -------------------------------------------------------------------- |
| `zodArray`              |       | Define a Zod array schema                                            |
| `zodCoerceNumber`       |       | Coerce and validate a numeric field, for form and query-string input |
| `zodDiscriminatedUnion` |       | Define a union discriminated by a literal field                      |
| `zodEnum`               |       | Define a Zod string enum schema                                      |
| `zodImport`             |       | Import the Zod schema builder                                        |
| `zodInputOutput`        |       | Derive the distinct input and output types of a transforming schema  |
| `zodObject`             | `zo`  | Define a Zod object schema                                           |
| `zodOptional`           |       | Add an optional field to a Zod object shape                          |
| `zodParseAsync`         |       | Parse data with asynchronous refinements                             |
| `zodSafeParse`          |       | Validate unknown data without throwing                               |
| `zodTransform`          |       | Define a schema that transforms its parsed text                      |

### Forms

| Prefix                 | Alias | Inserts                                                                                |
| ---------------------- | ----- | -------------------------------------------------------------------------------------- |
| `rhfController`        |       | Bind a non-native or wrapped input through Controller                                  |
| `rhfFormContextField`  |       | Read the surrounding FormProvider instead of threading props                           |
| `rhfFormProvider`      |       | Share one form instance with nested field components                                   |
| `rhfImport`            |       | Import a React Hook Form 7 API                                                         |
| `rhfImportZodResolver` |       | Import the Zod resolver                                                                |
| `rhfReset`             |       | Backfill a form once its data resolves, ignoring a response that arrives after unmount |
| `rhfSetError`          |       | Map a rejected submit onto both the offending field and a form-level root error        |
| `useFieldArray`        | `ufa` | Render a repeatable group of fields with stable keys                                   |
| `useForm`              | `uf`  | Register native fields and surface their validation messages                           |
| `useWatch`             | `uw`  | Subscribe to selected fields so only this subtree re-renders                           |

### Server state

| Prefix             | Alias | Inserts                                                                                             |
| ------------------ | ----- | --------------------------------------------------------------------------------------------------- |
| `queryAbortSignal` |       | Forward the query's AbortSignal so a superseded request is cancelled                                |
| `queryDependent`   |       | Hold a query until its input exists, so it never runs with an undefined key                         |
| `queryImport`      |       | Import a TanStack Query 5 API                                                                       |
| `queryOptimistic`  |       | Create an optimistic mutation whose rollback distinguishes a failed preparation from an empty cache |
| `queryOptions`     | `qo`  | Create reusable queryOptions for one resource                                                       |
| `queryPagination`  |       | Paginate while keeping the previous page visible during a fetch                                     |
| `queryPrefetch`    |       | Warm the cache on hover and focus so the next navigation renders immediately                        |
| `queryProvider`    |       | Create a stable QueryClient provider                                                                |
| `useInfiniteQuery` | `uiq` | Page through an infinite list, including the initialPageParam that TanStack Query 5 requires        |
| `useMutation`      | `um`  | Create a mutation that invalidates a cache key after success                                        |
| `useQuery`         | `uq`  | Render a query with its pending and error states                                                    |

### URL state

| Prefix                 | Alias | Inserts                                                                                            |
| ---------------------- | ----- | -------------------------------------------------------------------------------------------------- |
| `nuqsAdapter`          |       | Provide the adapter that nuqs 2 requires above any component using its hooks                       |
| `parseAsArrayOf`       |       | Parse a delimited query parameter into an array                                                    |
| `parseAsStringLiteral` |       | Restrict a query parameter to a fixed set of strings, rejecting anything else                      |
| `useQueryState`        |       | Sync one string state with a URL query parameter; the value is null when the parameter is absent   |
| `useQueryStates`       |       | Read and write several URL query parameters as one object, updating them in a single history entry |

### i18n

| Prefix                        | Alias | Inserts                                                                                                       |
| ----------------------------- | ----- | ------------------------------------------------------------------------------------------------------------- |
| `i18nChangeLanguage`          |       | Switch the active language                                                                                    |
| `i18nImportTrans`             |       | Import Trans from react-i18next for component interpolation                                                   |
| `i18nImportTranslation`       |       | Import Translation from react-i18next for the render-prop form                                                |
| `i18nImportUseTranslation`    |       | Import useTranslation from react-i18next                                                                      |
| `i18nInitJS`                  |       | Complete i18next 26 + react-i18next 17 local-resource setup                                                   |
| `i18nInitTS`                  |       | Complete i18next 26 + react-i18next 17 local-resource setup                                                   |
| `i18nResourceTypesTS`         |       | TypeScript resource augmentation for the local i18n module                                                    |
| `i18nSelectorTypesTS`         |       | TypeScript selector-mode augmentation for i18next 26.4+                                                       |
| `i18nTSelector`               |       | Translate with i18next selector syntax                                                                        |
| `i18nTrans`                   |       | Render a react-i18next Trans component with values and nested React content                                   |
| `i18nTranslateInterpolation`  |       | Translate a key with interpolation values                                                                     |
| `i18nTranslateNamespace`      |       | Translate a key from another namespace for one call, without changing the namespace bound by useTranslation   |
| `i18nTranslatePlural`         |       | Translate an i18next plural key with count                                                                    |
| `i18nTranslationRenderProp`   |       | Provide t to children through a render prop, for places where a hook cannot be used such as a class component |
| `i18nUseTranslationNamespace` |       | Get t and the i18n instance for one namespace                                                                 |

### Error boundaries

| Prefix                           | Alias | Inserts                                                                               |
| -------------------------------- | ----- | ------------------------------------------------------------------------------------- |
| `reactErrorBoundaryAsync`        |       | Forward an async event-handler failure to the nearest boundary                        |
| `reactErrorBoundaryComponentJSX` |       | Complete JavaScript React error boundary with an accessible fallback and reset action |
| `reactErrorBoundaryComponentTSX` |       | Complete TypeScript React error boundary with an accessible fallback and reset action |
| `reactErrorBoundaryFallbackJS`   |       | Create a fallbackRender callback for an ErrorBoundary                                 |
| `reactErrorBoundaryFallbackTS`   |       | Create a typed fallbackRender callback for an ErrorBoundary                           |
| `reactErrorBoundaryImport`       |       | Import ErrorBoundary from react-error-boundary 6                                      |
| `reactErrorBoundaryResetKeys`    |       | Create reset options for an ErrorBoundary                                             |

### Class names

| Prefix            | Alias | Inserts                                                                 |
| ----------------- | ----- | ----------------------------------------------------------------------- |
| `clsxConditional` |       | Compose conditional class names                                         |
| `clsxImport`      |       | Import clsx 2 for conditional class names                               |
| `cnUtilityJS`     |       | Complete JavaScript cn utility                                          |
| `cnUtilityTS`     |       | Complete TypeScript cn utility                                          |
| `twMergeClasses`  |       | Merge Tailwind utility classes and keep the winning conflict            |
| `twMergeImport`   |       | Import tailwind-merge 3 to resolve conflicting Tailwind utility classes |

### General hooks

| Prefix                 | ahooks | react-use | usehooks-ts | rooks |
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

### Tests

| Prefix                       | Alias | Inserts                                                                                  |
| ---------------------------- | ----- | ---------------------------------------------------------------------------------------- |
| `rtlAsyncUiJSX`              |       | Complete async UI test for Vitest 4, RTL 16, and user-event 14                           |
| `rtlAsyncUiTSX`              |       | Complete TypeScript async UI test for Vitest 4, RTL 16, and user-event 14                |
| `rtlComponentInteractionJSX` |       | Complete Vitest 4 + React Testing Library 16 + user-event 14 interaction test            |
| `rtlComponentInteractionTSX` |       | Complete TypeScript Vitest 4 + React Testing Library 16 + user-event 14 interaction test |
| `rtlQueryWrapperJSX`         |       | Create an isolated TanStack Query 5 wrapper for RTL tests                                |
| `rtlQueryWrapperTSX`         |       | Create an isolated TypeScript TanStack Query 5 wrapper for RTL tests                     |
| `rtlRenderHookJS`            |       | Complete hook interaction test using RTL 16 renderHook and Vitest 4                      |
| `rtlRenderHookTS`            |       | Complete TypeScript hook interaction test using RTL 16 renderHook and Vitest 4           |
| `testStoreResetJS`           |       | Reset a test store before each case                                                      |
| `testStoreResetTS`           |       | Reset a typed test store before each case                                                |

### Recipes

| Prefix               | Alias | Inserts                                                                                                |
| -------------------- | ----- | ------------------------------------------------------------------------------------------------------ |
| `reactFormMutation`  |       | Complete submit flow: validate, map a failed submit onto a root error, invalidate the list, then reset |
| `reactQueryBoundary` |       | Throw query failures to an error boundary and let QueryErrorResetBoundary drive the retry              |
| `reactQueryZod`      |       | Validate a service response at the query boundary, so bad data never reaches the component             |
| `reactSearchQuery`   |       | Debounced search whose cache key is the debounced term and whose fetch receives the query AbortSignal  |
| `rhfZodForm`         |       | Complete form file validated by one Zod schema                                                         |
| `zustandImmer`       |       | Complete typed store composing Immer drafts, persist partialize, and devtools in the correct order     |

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
