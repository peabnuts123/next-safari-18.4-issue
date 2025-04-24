This is a bug recreation for next.js issue [#78524](https://github.com/vercel/next.js/issues/78524).

The latest version of Safari (18.4) seems to freeze when devtools is opened when a project is using webpack.

## Reproduction steps

1. Be on latest MacOS Sequoia 15.4 and Safari 18.4
1. Create a new app with `npx create-next-app@latest`
    - I used the following settings. The only setting that seems to matter is that you choose Webpack for the bundler.
    ```
    ✔ What is your project named? … next-bug-safari-deleteme
    ✔ Would you like to use TypeScript? … Yes
    ✔ Would you like to use ESLint? … Yes
    ✔ Would you like to use Tailwind CSS? … Yes
    ✔ Would you like your code inside a `src/` directory? … Yes
    ✔ Would you like to use App Router? (recommended) … No
    ✔ Would you like to use Turbopack for `next dev`? … No
    ✔ Would you like to customize the import alias (`@/*` by default)? … Yes
    ✔ What import alias would you like configured? … @app/*
    ```
1. Run the app with `npm run dev`
1. Open the app in Safari (i.e. `http://localhost:3000`)
1. Observe the app loads fine
1. Open devtools (`Cmd+Opt+I`) and immediately type something (e.g. a bare number like `2`) into console
1. Try and send the command in console
1. Observe the browser is hanging
1. (5-10 seconds later) Observe the browser becomes responsive again and the problem resolves

You may also close + reopen devtools and notice this freeze happens each time.
