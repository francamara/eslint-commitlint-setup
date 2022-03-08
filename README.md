# eslint-commitlint-setup
Thanks to [Andrey Bejarano](https://github.com/andreybejarano/) for teaching me all this things

To make this work you must have the default formatter on VSCode 

In your config json file add this
```
  "[javascript]": {
    "editor.defaultFormatter": "vscode.typescript-language-features"
  },
```
## Dependencies required
May be outdated, check before using it
```
"devDependencies": {
  "@commitlint/cli": "^11.0.0",
  "@commitlint/config-conventional": "^11.0.0",
  "eslint": "^7.11.0",
  "eslint-config-standard": "^14.1.1",
  "eslint-plugin-import": "^2.22.1",
  "eslint-plugin-jasmine": "^4.1.1",
  "eslint-plugin-jest": "^24.1.0",
  "eslint-plugin-node": "^11.1.0",
  "eslint-plugin-promise": "^4.2.1",
  "eslint-plugin-standard": "^4.0.1",
}
```

## VSCode Plugins required
- [EditorConfig](https://marketplace.visualstudio.com/items?itemName=EditorConfig.EditorConfig)
- [EsLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)

# Commits
To standarize all commits, [Husky](https://www.npmjs.com/package/husky) is recommended too

## How to install Husky commit hooks
First, install husky as `devDependencies`
```
npm i -D husky
```
In your `package.json` add
```
"scripts": {
  (...)
  "prepare": "husky install"
}
```
Then
```
npm run prepare
```
For the pre-commit we want to check if the code format is following the standarized rules, so run
```
npx husky add .husky/pre-commit "npm run lint"
```
For the commit-msg we want to check that the commit message is following one of the rules shown before
```
npx husky add .husky/commit-msg "npx --no-install commitlint --edit $1"
```

## Commit message rules
You want all the commit messages to be like this: 

`{reason_to_commit}: {short explanation}`

Reasons to commit
```
[
  'build',
  'chore',
  'ci',
  'docs',
  'feat',
  'fix',
  'perf',
  'refactor',
  'revert',
  'style',
  'test'
]
```
Also, everything must be lowercase. You can check all the rules in the `commitlint.config.js` file