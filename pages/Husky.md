- #[[Frontend Tooling]]
- [Videotutorial](https://www.youtube.com/watch?v=U-R_882UGPM)
- ## Installation
	- 1. `npm install husky --save-dev`
	- 2. If your package.json is in same directory as your .git directory `npx husky install`
		- otherwise you can install husky in a custom directoy `npx husky install ~/project/.husky`
	- 3. You can add prepare lifecycle script into your package.json
		- ```json
		  "scripts": {
		    "prepare": "cd ~/project && husky install"
		  }
		  ```
		- the script will be run after npm install
	- 4. add a hook with `npx husky add .husky/pre-commit "npm test"`
		- you can also add a executable script in the .husky folder named after a git hook but you have to make shure that it is executable `chmod +x pre-commit`