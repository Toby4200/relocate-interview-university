#public-note 

My goal is to create test project for TypeScript on github
Where I want write algorithmic tasks from leetcode

Steps are
- [x] install typescript
- [x] configure debugger
- [x] create empty repository on github and publish
- [ ] add Jest for testing

## Links

- [[ How to Debug Node.js with TypeScript using Nodemon?]]
- Official node.js docs about [debugging](https://nodejs.org/en/docs/guides/debugging-getting-started)
- My GitHub repo with algorithms and [debugger](https://github.com/Toby4200/algorithms)


## Prerequesites
- node.js installation
- visual studio


## Installation of typeScript

https://www.typescriptlang.org/download

TypeScript is available as a [package on the npm registry](https://www.npmjs.com/package/typescript) available as `"typescript"`.

You will need a copy of [Node.js](https://nodejs.org/en/ "Link to the node.js project") as an environment to run the package. Then you use a dependency manager like [npm](https://www.npmjs.com/ "Link to the npm package manager"), [yarn](https://yarnpkg.com/ "Link to the yarn package manager") or [pnpm](https://pnpm.js.org/ "Link to the pnpm package manager") to download TypeScript into your project.

`npm install typescript ts-node --save-dev`


`npm install --save-dev nodemon`

## Install debugger in vs code

Nice article to configure debugger in vscode
[[How to Debug Node.js with TypeScript using Nodemon?]]

It's important to understand that if script running not as a process (express.js or koa for example)
to debug you need set debugger in code or breakpoint manually and launch script - **not attach**

It's because script end quickly


![[Pasted image 20230708192245.png]]


## Questions and answers

### why do i need ts-node

`ts-node` is a tool that's used to execute TypeScript code directly, without the need for a separate compilation step. Here are some reasons why you might want to use `ts-node`:

### how to disable error fail for typescript in developer mode

```zsh
TSError: ⨯ Unable to compile TypeScript:
src/index.ts:5:34 - error TS7006: Parameter 'rooms' implicitly has an 'any' type.
```

The error you're seeing is because TypeScript's strict type checking is enabled and it doesn't allow variables to have an implicit 'any' type. 

If you want to disable this behavior in development mode, you can do so by modifying your `tsconfig.json` file:
1. Open the `tsconfig.json` file.
2. Look for the `"compilerOptions"` section.
3. Set `"strict": false`, like so:

```json
{
  "compilerOptions": {
    // other options...
	"strict": false,
    // other options...
  }
}
```

This will tell TypeScript not to raise an error when a variable has an implicit 'any' type.

However, please note that using 'any' defeats the purpose of using TypeScript as it turns off a lot of its useful checks. It's generally better practice to specify types explicitly whenever possible.

### how to add debugger?

useful link
https://stackoverflow.com/questions/65556560/how-to-run-nodemon-with-typescript-in-debug-mode-in-webstorm

### how to kill by process

```zsh
 lsof -i :9229
 kill -9 <PID>
```

