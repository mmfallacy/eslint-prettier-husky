# ESLint, Prettier, Lint-Staged setup

### 1. Make sure to have a `package.json` and have initialized git in your project directory.

```bash
npm init
git init
```

### 2. Install needed dev dependencies.

```bash
npm install --save-dev eslint-config-prettier husky lint-staged
npm install --save-dev --save-exact prettier
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

```json
"extends": [
   /* other configs */,
   "prettier"
]
```

### 5. Set up husky for lint-staged.

```bash
npx husky install
npm pkg set scripts.prepare="husky install"
npx husky add .husky/pre-commit "npx lint-staged"
```

### 6. Set up lint-staged by adding the following to `package.json`.

```json
"lint-staged": {
  "*.{js,jsx,ts,tsx}": "eslint --fix",
  "**/*": "prettier --write --ignore-unknown"
}
```

### Additional:

- To set up a Prettier configuration, create a `.prettierrc` file.
- To exclude files from being formatted by Prettier, create a `.prettierignore` file.
- The `"lint-staged"` object in `package.json` can be moved into a `.lintstagedrc` file.