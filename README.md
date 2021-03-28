Reason React Hacker News Compiled with [Melange](https://github.com/melange-re/melange)
===

Hacker News mobile app built with [Reason React](https://github.com/reasonml/reason-react)

See it at https://hackernewsmobile.com

Source is in [src/](src/), starting from [src/index.re](src/index.re)

You can run the app locally with `yarn start`

Build for deployment with `NODE_ENV=production yarn build`

Add melange `esy.json` with `npx melange-deps`.

Change `package.json` `bs-platform` version to `bs-platform:"*"`
Install npm deps with `yarn`.

Add `action-plugin` to `dune-project` to fix `dynamic-run` error:

```dune
(lang dune 2.8)
(using action-plugin 0.1)
```

Install esy deps with `esy install`.

Change `package.json` build command to `"bsb-build": "esy bsb -make-world",`

# Error - How do we fix this?
Running `yarn bsb-build` or `esy bsb -make-world -- --display=short` from terminal get you:

```sh
[I] ➜ esy bsb -make-world -- --display=short
bsb_parse_depend node_modules/reason-react/src/legacy/ReasonReact.cmi
bsb_parse_depend node_modules/reason-react/src/legacy/ReactEventRe.cmi
bsb_parse_depend node_modules/reason-react/src/legacy/ReactDOMServerRe.{cmi,cmj,js}
bsb_parse_depend node_modules/reason-react/src/legacy/ReactDOMRe.{cmi,cmj,js}
bsb_parse_depend node_modules/reason-react/src/legacy/ReasonReactCompat.cmi
Error: Multiple rules generated for
_build/default/node_modules/reason-react/src/React.js:
- file present in source tree
- dune.bsb:15
Hint: rm -f node_modules/reason-react/src/React.js
```
