# **Fastify TypeScript Starter Project**

A starter template for building robust server-side applications using **Fastify** with **TypeScript**. This repository is designed for scalability, readability, and best practices. Includes integration with **Prettier**, **ESLint**, and **Typedoc** for a well-maintained codebase.

---

## **Features**

- 🚀 **Fastify**: A high-performance web framework.
- 🛠 **TypeScript**: Type-safe development with strict configurations.
- 🎨 **Prettier**: Automatic code formatting for a consistent style.
- 🔍 **ESLint**: Linting for cleaner and error-free code.
- 📚 **Typedoc**: Generate documentation for your code.
- 🗂 **Path Aliases**: Simplified imports using `@src`, `@routes`, `@services`, etc.
- 🔄 Development and production-specific TypeScript configurations.

---

## **Dependencies**

These are the essential libraries required for running the application in production:

| **Dependency**       | **Version** | **Description**                                                                                     |
|-----------------------|-------------|-----------------------------------------------------------------------------------------------------|
| `dotenv`             | ^16.4.5    | Loads environment variables from a `.env` file.                                                    |
| `fastify`            | ^5.1.0     | Fast and low-overhead web framework for Node.js.                                                   |
| `fastify-plugin`     | ^5.0.1     | A plugin system for extending Fastify functionality.                                               |
| `mongodb`            | ^5.9.2     | MongoDB driver for Node.js.                                                                        |
| `nanoid`             | ^5.0.8     | A tiny, secure URL-friendly unique string ID generator.                                            |
| `pg`                 | ^8.13.1    | PostgreSQL client for Node.js.                                                                     |
| `pino-pretty`        | ^13.0.0    | Prettifies `pino` logs for easier readability during development.                                  |
| `rotating-file-stream` | ^3.2.5   | File stream rotation for logging.                                                                  |
| `typeorm`            | ^0.3.20    | A modern ORM for TypeScript and JavaScript (supports PostgreSQL, MySQL, etc.).                     |
| `uuid`               | ^11.0.3    | A library for generating unique identifiers.                                                       |
| `zod`                | ^3.23.8    | TypeScript-first schema validation with static type inference.                                     |

---

## **DevDependencies**

These are the tools and libraries required for development and testing purposes:

### **Code Quality & Linting**

| **Dependency**              | **Version** | **Description**                                                                 |
|------------------------------|-------------|---------------------------------------------------------------------------------|
| `eslint`                   | ^9.15.0    | Linting tool for identifying and fixing problems in JavaScript and TypeScript. |
| `eslint-config-prettier`   | ^9.1.0     | Disables ESLint rules that conflict with Prettier.                             |
| `eslint-plugin-import`     | ^2.31.0    | Ensures proper imports and prevents issues with ES module syntax.             |
| `eslint-import-resolver-typescript` | ^3.6.3 | Resolves TypeScript paths for ESLint.                                         |
| `typescript-eslint`        | ^8.16.0    | ESLint plugin for TypeScript linting rules.                                    |

### **Code Formatting**

| **Dependency**         | **Version** | **Description**                                         |
|-------------------------|-------------|---------------------------------------------------------|
| `prettier`            | ^3.3.3     | Code formatter for consistent code style.              |

### **TypeScript**

| **Dependency**         | **Version** | **Description**                                         |
|-------------------------|-------------|---------------------------------------------------------|
| `typescript`          | ^5.7.2     | TypeScript compiler for static type-checking.           |
| `ts-node`             | ^10.9.2    | Run TypeScript files directly in Node.js.               |
| `tsc-alias`           | ^1.8.10    | Replaces TypeScript paths in the transpiled JavaScript. |
| `tsc-watch`           | ^6.2.1     | Re-compiles TypeScript files on changes during development. |
| `tsconfig-paths`      | ^4.2.0     | Resolves paths defined in `tsconfig.json` during runtime.|

### **Testing**

| **Dependency**        | **Version** | **Description**                                           |
|------------------------|-------------|-----------------------------------------------------------|
| `jest`               | ^29.7.0    | JavaScript testing framework.                            |
| `@types/jest`        | ^29.5.14   | TypeScript definitions for Jest.                        |

### **Build Tools**

| **Dependency**       | **Version** | **Description**                                           |
|-----------------------|-------------|-----------------------------------------------------------|
| `rimraf`             | ^6.0.1    | Cross-platform tool to remove files or directories.      |

### **Development Tools**

| **Dependency**       | **Version** | **Description**                                           |
|-----------------------|-------------|-----------------------------------------------------------|
| `concurrently`      | ^9.1.0     | Run multiple npm scripts concurrently.                   |
| `nodemon`           | ^3.1.7     | Automatically restarts the server when file changes are detected. |
| `husky`             | ^9.1.6     | Git hooks for running linting or tests before commits.    |
| `lint-staged`       | ^15.2.10   | Run linters on staged files before committing.            |

### **Documentation**

| **Dependency**            | **Version** | **Description**                                          |
|----------------------------|-------------|----------------------------------------------------------|
| `typedoc`                | ^0.27.2    | Documentation generator for TypeScript projects.         |


## **Project Setup**

### **1. Clone the Repository**
```bash
git clone https://github.com/bkapilsharmadev/fastify-typescript-sample.git
cd fastify-typescript-sample
```

### **2. InstallDependencies**
```bash
npm install
```

### **3. Run the project**
- For Development
```bash
npm run dev
```
- For Production
```bash
npm run build && npm start
```

### **4. Scripts**
| Script         | Command                                                       | Purpose                                                                                                 |
|----------------|---------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| `clean`        | `rimraf dist`                                                 | Deletes the `dist` directory to ensure a clean build environment.                                       |
| `build:dev`    | `tsc -p tsconfig.dev.json && tsc-alias`                       | Compiles TypeScript in development mode using `tsconfig.dev.json` and resolves path aliases.            |
| `build:prod`   | `tsc -p tsconfig.prod.json && tsc-alias`                      | Compiles TypeScript in production mode using `tsconfig.prod.json` and resolves path aliases.            |
| `start`        | `npm run build:prod && node dist/index.js`                    | Builds the project in production mode and starts the application.                                       |
| `dev`          | `tsc-watch -p tsconfig.dev.json --onSuccess \"npm run start:alias\"`             | Lints, formats, and starts the application in watch mode for development.                               |
| `start:alias`  | `tsc-alias -p tsconfig.dev.json && nodemon dist/index.js`     | Resolves path aliases and starts the server with `nodemon` for live reloads.                            |
| `lint`         | `eslint src`                                                  | Lints the codebase using ESLint to ensure code quality and style consistency.                           |
| `format`       | `prettier --write src/**/*.ts`                                | Formats the codebase using Prettier to maintain a consistent style.                                     |
| `prepare`      | `husky`                                                       | Runs Husky setup to enable Git hooks for tasks like pre-commit linting or formatting.                   |


## Project Configuration Files

| **File**                | **Description**                                                                 |
|--------------------------|---------------------------------------------------------------------------------|
| `.gitignore`            | Specifies files and directories to ignore in the version control system (Git).  |
| `.prettierignore`(#prettier-ignore-file)       | Lists files and directories to ignore during Prettier formatting.               |
| `.prettierrc`           | Configuration file for Prettier, defining code formatting rules.                |
| `eslint.config.mjs`     | ESLint configuration file for linting the codebase.                             |
| `package.json`          | Contains project metadata, dependencies, and scripts for running the project.   |
| `tsconfig.dev.json`     | TypeScript configuration file for development builds.                           |
| `tsconfig.json`         | Base TypeScript configuration file for the project.                             |
| `tsconfig.prod.json`    | TypeScript configuration file for production builds.                            |
| `typedoc.json`          | Configuration file for generating project documentation using Typedoc.          |


## Prettier Ignore File

The `.prettierignore` file specifies which files and directories should be ignored by Prettier during formatting. Below is the configuration used in this project:

```plaintext
node_modules/  # Ignore the node_modules folder
dist/          # Ignore the compiled TypeScript output folder
*.config.js    # Ignore configuration files with .config.js extension
```

## ESLint Configuration

Below is the ESLint configuration file used in this project, with inline comments explaining each section:

```javascript
// @ts-check
import eslint from "@eslint/js";
import tseslint from "typescript-eslint";
import jest from "eslint-plugin-jest";
import * as importPlugin from "eslint-plugin-import";

export default tseslint.config(
  {
    // Ignore specific directories
    ignores: ["node_modules", "build"],
  },
  {
    // Apply to TypeScript files in the src directory
    files: ["src/**/*.{ts,tsx}"], // Matches all TypeScript files
  },
  {
    // Special settings for JavaScript files (CommonJS)
    files: ["src/**/*.js"],
    languageOptions: {
      sourceType: "commonjs", // Set source type to CommonJS for JavaScript files
    },
  },
  // Recommended ESLint and TypeScript configs
  eslint.configs.recommended,
  ...tseslint.configs.strictTypeChecked,
  ...tseslint.configs.stylisticTypeChecked,

  {
    // Language options for TypeScript
    languageOptions: {
      parserOptions: {
        projectService: true, // Enable project services for better type checking
        tsconfigRootDir: import.meta.dirname, // Locate tsconfig file in the project root
      },
    },
  },
  {
    files: ["tests/**/*.js"], // Specific rules for test files
    ...jest.configs["flat/recommended"], // Apply Jest recommended configurations
    rules: {
      ...jest.configs["flat/recommended"].rules,
      "jest/prefer-expect-assertions": "off", // Disable the rule that enforces expect assertions
    },
  },
  {
    // Include the import plugin
    plugins: {
      import: importPlugin, // Helps with managing imports and exports
    },
    // Custom rules
    rules: {
      "@typescript-eslint/no-unused-vars": "warn", // Warn for unused variables
      "import/extensions": [
        "error", // Enforce extensions in import statements
        "always",
        {
          js: "always",
          ts: "always",
          jsx: "always",
          tsx: "always",
        },
      ],
    },
  },
);
```