# Upload Project to Github

Share the new project on github through the VCS menu:
```bash
Git > GitHub > Share Project on GitHub
#Choose all the files for the initial commit

#After you have created the repository on github, 
# create a new dev branch
git checkout -b dev

#set the upstream branch so you can push to the dev branch
git push --set-upstream origin dev
```

Now you can safely work on the dev branch and push your changes to github.
With the dev branch, you can create a pull request to the master branch when you are done with your changes.

The server will automatically deploy the dev/prod branches using a cron job.

![Step 5](../images/step5.png)

<div align="right">
<a href="https://github.com/agaktr/workflows/blob/master/steps/step6.md" align="right">Next: Setup the Dev server</a>
</div>  
