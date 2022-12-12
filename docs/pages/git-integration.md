
## Integration with Git
We are going to upload our code to github in a later section.<br>
For now, let's just init our git repository.<br>
Run this: <br>
`git init`

Copy this to a `.gitignore` file:

```
node_modules/
.idea
venv*/
.serverless/*
volume/*
```

Run this: ` git add *`

And let's commit `git commit -m "initial commit"`