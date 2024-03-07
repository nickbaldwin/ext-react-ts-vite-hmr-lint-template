# Extension Starter

## What does this extension do?

Not much. It has enough to prove the build and tooling works. 

## How does it work?



## How does the extension work?

The extension is composed of four primary components:

-   #### Manifest

    This mandatory JSON file defines the configuration, permissions and metadata for the extension.

-   #### Content scripts

    The main content script injects the extension 'App' into the context of search results pages across all Monster domains. While it can access and modify the DOM, it operates in an isolated context which means it cannot access key data added by the Monster site (Window properties and React element info). Thus, a 'world' script is injected into the Monster web page as a script tag purely in order to pass this information to the content script.

-   #### Service worker

    This script runs in the background, and communicates with the content scripts running on all search pages, in order to sync and correctly persist settings used across all Monster domains.

-   #### Popup
    The popup page simply provides some basic information so that newbies can be directed to the documentation.

In addition, there are numerous assets and build/configuration files that are used to generate the extension. This is described in the build process section.

## How is it developed?

This extension is developed in React and TypeScript, and uses Vite as the build tool. It also uses the CRXjs Vite plugin to simplify the development/build process for extensions (particularly HMR or Hot Module Replacement).

## Linting & Formatting

ESLint, Prettier, Husky, Lint-staged


## To consider

## Expanding the ESLint configuration

If you are developing a production application, we recommend updating the configuration to enable type aware lint rules:

-   Configure the top-level `parserOptions` property like this:

```js
export default {
    // other rules...
    parserOptions: {
        ecmaVersion: 'latest',
        sourceType: 'module',
        project: ['./tsconfig.json', './tsconfig.node.json'],
        tsconfigRootDir: __dirname,
    },
};
```

-   Replace `plugin:@typescript-eslint/recommended` to `plugin:@typescript-eslint/recommended-type-checked` or `plugin:@typescript-eslint/strict-type-checked`
-   Optionally add `plugin:@typescript-eslint/stylistic-type-checked`
-   Install [eslint-plugin-react](https://github.com/jsx-eslint/eslint-plugin-react) and add `plugin:react/recommended` & `plugin:react/jsx-runtime` to the `extends` list

https://github.com/prettier/prettier
https://github.com/prettier/eslint-config-prettier
https://github.com/lint-staged/lint-staged
https://github.com/typicode/husky
