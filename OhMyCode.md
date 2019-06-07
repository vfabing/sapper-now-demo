# Start coding on Sapper

`npx degit "sveltejs/sapper-template#webpack" sapper-demo`

`cd sapper-demo`

`npm i`

`npm run dev`

# Start deploying on Now.sh

`npm i now-sapper`

Add file `now.json` with content:
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

`npm run build`

`now`