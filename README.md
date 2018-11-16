# Angular Language Service as a TypeScript plugin extension for Visual Studio Code

[Visual Studio Code extension](https://marketplace.visualstudio.com/items?itemName=cyrilletuzi.typescript-angular-plugin)
activating the official Angular Language Service as a TypeScript plugin.

As a reminder, the Language Service is an official tool provided by Angular to give you **assistance and error-checking in templates**.

## Why?

Until now, you used [the official Angular Language Service extension for VS Code](https://marketplace.visualstudio.com/items?itemName=Angular.ng-template). So why this one?

### More efficient

The legacy official extension launches a duplicate TypeScript process,
while this extension launches the same Angular Language Service but as a TypeScript plugin,
which is **more efficient**!

This extension works exactly in the same way as the new official
[TypeScript TSLint plugin extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode.vscode-typescript-tslint-plugin)
from Microsoft.

### Up to date

As asked and answered in [angular/vscode-ng-language-service#298](https://github.com/angular/vscode-ng-language-service/issues/298),
the legacy official extension is not really maintened anymore, and so have a lot of issues.

This extension is directly using the latest official `@angular/language-service` package,
so it's **up to date** and it will be updated at each new release of `@angular/language-service` (including patches).

## By the same author

- [Angular schematics extension for VS Code](https://marketplace.visualstudio.com/items?itemName=cyrilletuzi.angular-schematics) (GUI for Angular CLI commands)
- [@ngx-pwa/local-storage](https://github.com/cyrilletuzi/angular-async-local-storage): 1st Angular library for local storage
- Library [@ngx-pwa/offline](https://github.com/cyrilletuzi/ngx-pwa-offline)
- Popular [Angular posts on Medium](https://medium.com/@cyrilletuzi)
- Follow updates of this lib on [Twitter](https://twitter.com/cyrilletuzi)
- **[Angular onsite trainings](https://formationjavascript.com/formation-angular/)** (based in Paris, so the website is in French, but [my English bio is here](https://www.cyrilletuzi.com/en/web/) and I'm open to travel)

## Getting started

Follow instructions on [Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=cyrilletuzi.typescript-angular-plugin),
or just search for **"Angular Language Service as a TypeScript plugin"** by "Cyrille Tuzi" directly inside VS Code extensions panel. Done.

## Requirements

1. This extension supports **Angular >= 6**.

2. To avoid noise in non-Angular projects, this extension is only enabled inside an Angular CLI project,
ie. **with an `angular.json` file in workspace**.

3. If you already have the legacy extension, disable it.

4. This kind of extensions are designed to work with **the VS Code version of TypeScript**
(which is the default configuration). If you switched to the workspace version of TypeScript,
you can have the same behavior by adding this to your `tsconfig.json`:

```json
{
    "compilerOptions": {
        "plugins": [{ "name": "@angular/language-service" }]
    }
}
```

## Inline templates

For now, **the extension only works with inline templates**. Support for external templates is being investigated (see [#1](https://github.com/cyrilletuzi/vscode-typescript-angular-plugin/issues/1) if you want to help).

It's a good occasion to switch to inline templates. Here are some reasons why:

### Classic scenario

Despite it's not the default configuration in Angular CLI,
the official `@angular/language-service` is designed to work with inline templates.

Angular is the only major framework doing external templates. **Vue and React templates are inlined.**

### Separation of concerns

**Separation of concerns doesn't imply separation of files.**

Putting a color in your class, that would be breaking the separation of concerns.
But guess what: such crazy things are possible with external templates too. ;)

### Easier to understand

Externalizing CSS is a good idea, as it's static and can be quite long.

But there is a very direct relation between your HTML template and your TypeScript class,
because of data bindings. **External templates make it difficult to understand these bindings**,
especially for new Angular developers.

### Single responsibility principle

Finally, I come to what you're screaming at from the beginning: "HTML templates can be long too,
so the TypeScript files become a mess with inline templates".

Well, if your templates are long, the mess may be how you program (sorry!), as you don't respect one of the major principles of programming:
the **single responsibility principle**.

**Inline templates favors to pay attention to keep components small**, which is *good*,
while external templates favors huge components, which is *bad*.

So yes, **the good practice is inline templates! :)**

### How?

For a new project:

```bash
ng new --inlineTemplate
```

For an existing project, add this in `angular.json`:

```json
{
  "projects": {
    "yourprojectname": {
      "schematics": {
        "@schematics/angular:component": {
          "inlineTemplate": true
        }
      }
    }
  }
}
```

## Release Notes

[Changelog available here](https://github.com/cyrilletuzi/vscode-typescript-angular-plugin/blob/master/CHANGELOG.md).

## License

MIT