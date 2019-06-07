# Start coding on Sapper [DEPRECATED. Please have a look to [sapper-now-template](https://github.com/vfabing/sapper-now-template)]
https://sapper.svelte.dev/

`npx degit "sveltejs/sapper-template#webpack" sapper-demo`

`cd sapper-demo`

`npm i`

`npm run dev`

# Start deploying on Now.sh
https://sapper.svelte.dev/docs#Deploying_to_Now

## Install Now CLI
`npm install -g now`

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
`npm run build`

`now`

# Annexes

## Fix webpack.config.js

[CHANGE] `external: Object.keys(pkg.dependencies).concat(` to `external: [].concat(`

## Fix server.js (Expose polka handler)
[CHANGE] 
`polka()` to `const app = polka()` 

[REMOVE]
```javascript
	.listen(PORT, err => {
		if (err) console.log('error', err);
	});
```

[ADD] `export default app.handler`

[ADD]
```javascript
if (!process.env.NOW_REGION) {
	app.listen(PORT, err => {
		if (err) console.log('error', err)
	})
} 
```
