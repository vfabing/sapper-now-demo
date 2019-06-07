# Start coding on Sapper
https://sapper.svelte.dev/

`npx degit "sveltejs/sapper-template#webpack" sapper-demo`

`cd sapper-demo`

`npm i`

`npm run dev`

# Start deploying on Now.sh
https://sapper.svelte.dev/docs#Deploying_to_Now

## Add file `now.json` with content:
```json
{
    "version": 2,
    "name": "sapper-demo",
    "alias": "sapper-demo",
    "builds": [
      {
        "src": "__sapper__/build/index.js",
        "use": "now-sapper"
      }
    ],
    "routes": [{ "src": "/(.*)", "dest": "__sapper__/build/index.js" }]
  }
```

## Build & Deploy
`npm run build & now`

# Annexes

## Fix webpack.config.js

`external: Object.keys(pkg.dependencies).concat(` to `external: [].concat(`

## Fix server.js (Expose polka handler)
`polka()` to `const app = polka()` 

`export default app.handler`
