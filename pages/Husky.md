- #[[Frontend Tooling]]
- [Videotutorial](https://www.youtube.com/watch?v=U-R_885UGPM)
- all husky does is change the directory where your hook scripts are stored
- ## Installation
	- 4. `npm install husky --save-dev`
	- 5. If your package.json is in same directory as your .git directory `npx husky install`
		- otherwise you can install husky in a custom directoy `npx husky install ~/project/.husky`
	- 6. You can add prepare lifecycle script into your package.json
		- ```json
		  "scripts": {
		    "prepare": "cd ~/project && husky install"
		  }
		  ```
		- the script will be run after npm install
		- if you don't want to autoinstall you can give it another name and just run the script when you need the hooks
	- collapsed:: true
	  7. add a hook with `npx husky add .husky/pre-commit "npm test"`
		- you can also add a executable script in the .husky folder named after a git hook but you have to make shure that it is executable `chmod +x pre-commit`
- ## useful scripts
	- ### prepare-commit-msg check for Jira ID
		- ```bash
		  #!/usr/bin/env bash
		  . "$(dirname -- "$3")/_/husky.sh"
		  
		  # Git Hook for JIRA_TASK_ID
		  # Adds to the top of your commit message `JIRA_TASK_ID`, based on the prefix of the current branch `feature/AWG-562-add-linter`
		  # Example: `Add SwiftLint -> `AWG-562 Add SwiftLint
		  
		  if [ -z "$BRANCHES_TO_SKIP" ]; then
		    BRANCHES_TO_SKIP='master feature'
		  fi
		  
		  CURRENT_BRANCH=$(git branch --show-current)
		  for BRANCH in $BRANCHES_TO_SKIP; do
		    if [ "$BRANCH" = "$CURRENT_BRANCH" ]; then
		      echo "Info, skipping Jira ID check since current branch is included in the 'BRANCHES_TO_SKIP' variable"
		      exit 0
		    fi
		  done
		  
		  COMMIT_FILE=$1
		  COMMIT_MSG=$(cat "$1")
		  CURRENT_BRANCH=$(git rev-parse --abbrev-ref HEAD)
		  JIRA_ID_REGEX="[A-Z0-9]{1,10}-?[A-Z0-9]+"
		  JIRA_ID_IN_CURRENT_BRANCH_NAME=$(echo "$CURRENT_BRANCH" | { grep -Eo "$JIRA_ID_REGEX" || true; })
		  JIRA_ID_IN_COMMIT_MESSAGE=$(echo "$COMMIT_MSG" | { grep -Eo "$JIRA_ID_REGEX" || true; })
		  
		  if [ -n "$JIRA_ID_IN_COMMIT_MESSAGE" ]; then
		    if [ "$JIRA_ID_IN_COMMIT_MESSAGE" != "$JIRA_ID_IN_CURRENT_BRANCH_NAME" ]; then
		      echo "Error, your commit message JIRA_TASK_ID='$JIRA_ID_IN_COMMIT_MESSAGE' is not equal to current branch JIRA_TASK_ID='$JIRA_ID_IN_CURRENT_BRANCH_NAME'"
		      exit 1
		    fi
		  elif [ -n "$JIRA_ID_IN_CURRENT_BRANCH_NAME" ]; then
		    echo "$JIRA_ID_IN_CURRENT_BRANCH_NAME $COMMIT_MSG" > "$COMMIT_FILE"
		    echo "JIRA ID '$JIRA_ID_IN_CURRENT_BRANCH_NAME', matched in current branch name, prepended to commit message. (Use --no-verify to skip)"
		  fi
		  ```
		- checks if the branch name contains a Jira Id. If so it checks if the Jira Id of the branch name and the Jira Id of the commit message are the same
		- if the branch name contains a jira Id and the commit message not it adds the Jira Id of the branch name to the commit message
	- ### pre-push run unit tests and linters
		- ```bash
		  #!/usr/bin/env sh
		  . "$(dirname -- "$3")/_/husky.sh"
		  
		  # runs frontend unit tests and linters
		  cd ~/project/ && npm run test:prod && npm run lint:js && npm run lint:style
		  
		  ```
		- goes to the directory of the package.json and runs the unit tests and linting scripts
- ## Tipps
	- If you use the GUI of Intellij to commit and push you can see the Errors in the notification panel or in the Git console
	  ![image_1704370066083_0](../assets/image_1704370066081_0.png){:height 373, :width 455}
	- ![image.png](../assets/image_1704370110492_0.png){:height 300, :width 685}
	-
	- If you want to skip a hook you can add the `--no-verify` flag to your git command for example `git commit --no-verify`
- ## Uinstall
	- `npm uninstall husky && git config --unset core.hooksPath`
-