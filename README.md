# ESLint, Prettier, Lint-Staged setup

### 1. Make sure to have a `package.json` and have initialized git in your project directory.

### 2. Install needed dev dependencies.

```bash
npm install -D eslint-config-prettier husky lint-staged
npm install -D -E prettier
```

### 3. Install and set up eslint.

```bash
npm init @eslint/config
```

> Recommended options:
>
> - **How would you like to use ESLint?:** To check syntax, find problems, and enforce code style
> - **What type of modules does your project use?:** JavaScript modules (import/export)
> - **How would you like to define a style for your project?:** Use a popular style guide
> - **Which style guide do you want to follow?:** Airbnb
> - **What format do you want your config file to be in?:** JSON
> - **Would you like to install them (dependencies) now?:** Yes

### 4. Add `"prettier"` to the `"extends"` array in the `.eslintrc.*` file.

Make sure to put it **last**, so it overrides other configs.

```js
"extends": [
   /* other configs */,
   "prettier"
]
```

### 5. Set up husky.

```bash
npx husky-init && npm install
```

### 6. Set up lint-staged by adding the following to `package.json`.

```js
{
  // ...
  "scripts": {
    // ...
    "test": "npx lint-staged"
  },
  "lint-staged": {
    "*.{js,jsx,ts,tsx}": "eslint --fix",
    "**/*": "prettier --write --ignore-unknown"
  }
  // ...
}
```

### Additional:

- To set up a Prettier configuration, create a `.prettierrc` file.
- To exclude files from being formatted by Prettier, create a `.prettierignore` file.
- The `"lint-staged"` object in `package.json` can be moved into a `.lintstagedrc.json` file.
```js
// .lintstagedrc.json
{
  "*.{js,jsx,ts,tsx}": "eslint --fix",
  "**/*": "prettier --write --ignore-unknown"
}
```
