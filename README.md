# Next.js 16.3+ declarations need TypeScript 6

```sh
npm install
npm run typecheck
```

The only source file is a typed `next.config.ts`. With TypeScript 5.9.3 and `skipLibCheck: false`, `tsc --noEmit` reports 7 errors, all from `next/dist/server/web/spec-extension/url-pattern.d.ts`:

```
node_modules/next/dist/server/web/spec-extension/url-pattern.d.ts(2,17): error TS2304: Cannot find name 'URLPatternInput'.
node_modules/next/dist/server/web/spec-extension/url-pattern.d.ts(2,67): error TS2304: Cannot find name 'URLPatternOptions'.
node_modules/next/dist/server/web/spec-extension/url-pattern.d.ts(2,87): error TS2304: Cannot find name 'URLPattern'.
...
```

Same project, no errors:

- with `typescript@6.0.3`
- with `next@16.2.0` (the declaration was `declare const GlobalURLPattern: any` there)
