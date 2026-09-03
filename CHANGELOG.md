# Changelog / 更新日志

## 1.1.1 (2026-09-03)

- Publish extension to Open VSX Registry alongside the VS Code Marketplace
- Update CI workflow to build the VSIX package once and reuse it across both marketplaces

## 1.1.0 (2026-09-03)

- Unify packaging and publishing scripts to `vsce:package` and `vsce:publish`
- Update GitHub Actions CI workflow to use `pnpm run vsce:publish`

## 1.0.2

- No snippet changes.
- The test suite now validates the snippet sources themselves — required fields, known `scope` language ids, balanced `${…}` placeholders and unique names — instead of parsing the expanded code. What a snippet expands to in a real file is settled in the editor, not here.

## 1.0.0

- Initial standalone React ecosystem snippet collection for JavaScript, JSX, TypeScript and TSX.
- Cover Immer, Zustand, Zod, React Hook Form, TanStack Query, i18next, ahooks, error boundaries, class names and React testing.
- Include six focused integration recipes, scoped language variants and separate import snippets.
- Validate source contracts, expanded syntax, real dependency types, representative behavior and VSIX contents.
