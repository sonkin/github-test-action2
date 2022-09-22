##Github workflow demo

### Workflow and test

In folder `./github/workflows/test.yaml` you can see the description of the workflow.
It should be executed on any **pull request** in branch **test**:
```
on:
  pull_request:
    __branches: [test]__
```
And it will check that all tests will pass.

The idea is to demonstrate how to create a pull request, and check should fail, and then succeed.

Test in `App.test.js` is checking 

For that, change 

###Preparing

You need to generate a new Personal Access Token with the workflow scope enabled in GitHub and configure your application to use that.

**Background**: third-party tools with GitHub integrations like IntelliJ, Visual Studio Code, Github Desktop etc use tokens to connect to your GitHub account so they can pull/push etc on your behalf. In the case of IntelliJ, their instructions only say to include the repo, the gist and the read:org scopes. But you need the workflow scope to modify GitHub Actions.

####Here's how to fix it:

1) In your Github account, go to **Settings** (in your avatar dropdown in the top right-hand corner)
2) Go to **Developer Settings > Personal Access Tokens**
3) If your application is listed, click on its name to edit the settings associated with its token. Make sure workflow is ticked.
4) Click on **Update Token** to save the change.
5) On the same page, click on **Generate Token**. Read the information carefully, then click OK to continue.
6) Copy the new token that Github shows you.
7) You will need to recreate your application's integration with Github using the new token for the change to take effect.

**Note:** you may be able to skip steps 5 onward if your application refreshes its permissions automatically, but that didn't seem to work for me with IntelliJ.

In IntelliJ, the last step was to go to **Settings > Version Control > GitHub**, then remove the existing integration and re-add it, pasting in the new token. You'll have to find out what needs to be done for the tool you're using to give it the new GitHub Personal Access Token.



### Running

git remote set-url origin https://github.com/sonkin/github-test-action2.git

git push -u origin test

git push origin HEAD

git push -f origin test

1) Now you should create a new branch.
2) Then make a change in the code
3) Commit this change in a new branch
4) In IDE select Git > GitHub > Create Pull Request
5) Base branch should be `test` (or other name for the HEAD branch)
6) Enter the title and create Pull Request
7) WebStorm should show the link to new PR
8) Open it, and see that workflow is working and checking the code
9) After some time it will finish and show the result

