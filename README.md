# Assert Never [![npm version][npm-image]][npm-url]

Helper function for [exhaustive checks][exhaustive-checks] of discriminated
unions in TypeScript.

## Installation for npm

```
npm install --save assert-never
```

## Usage for Deno

```ts
import {assertNever} from "https://deno.land/x/assert_never@v1.2.2/mod.ts";

type A = {type: 'a'};
type B = {type: 'b'};
type Union = A | B;

function doSomething(arg: Union) {
  if (arg.type === 'a') {
    return something;
  }

  if (arg.type === 'b') {
    return somethingElse;
  }

  // TS will error if there are other types in the union
  // Will throw an Error when called at runtime. Use `assertNever(arg, true)`
  // instead to fail silently.
  return assertNever(arg);
}
```

[npm-image]: https://badge.fury.io/js/assert-never.svg
[npm-url]: https://badge.fury.io/js/assert-never
[exhaustive-checks]: https://basarat.gitbooks.io/typescript/docs/types/discriminated-unions.html#exhaustive-checks
