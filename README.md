# ESLint, Prettier, Husky Set up

[Resource](https://www.youtube.com/watch?v=oWty0Nw1ydk)

1. Create a new node project.

2. Install **husky** `npx husky-init` (and install the dependencies)

   > Husky is a JavaScript and Git tooling that makes configuring Git hooks easy.

3. Install **lint-staged**

   >Lint-staged is a tool that can execute multiple commands (typically linters) against staged git files.

4.  Open `.\husky\pre-commit` and add `yarn lint-staged`. This runs lint-staged before every commit.

5. Install **ESLint** and **Prettier** extensions for VSCode.

> ESLint is a linter that analyzes your code for possible problems and bad practices.
>
> Prettier is a code formatter that enforces good coding practices.

6. Install `eslint` and `prettier` as dev dependencies.

7. Set up an `eslint` configuration file by passing the `--init` flag to `eslint` and answer the prompts

   > Recommended options:
   >
   > - To check syntax, find problems, and enforce code style
   >   - This ensures that ESLint works at full capacity (conflicts with prettier will be addressed later)
   > - JavaScript modules (import/export )
   > - *Pick whichever suites your case*
   > - Typescript: No
   > - Browser (for projects that use front-end frameworks); Node (for projects that are server-side)
   > - Use a popular style guide
   > - Airbnb
   > - JSON
   > - Yes

8. Set up a `prettier` configuration file by creating a `.prettierrc` file.

9. Install `eslint-config-prettier` to disable rules that eslint and prettier has conflicts on.

   > You may need to add `"prettier"` after the `"airbnb-base"` in your `.eslintrc.json` file.

8. Add a `"lint-staged"` key to your `package.json` that contains your specified file glob pattern, and the array of commands you want to run when these files are staged.

   ```json
   ...
   	"lint-staged" : {
           "**/*.{js,jsx,ts,tsx}": [
               "eslint",
               "prettier --write"
           ]
       }
   ```

   

