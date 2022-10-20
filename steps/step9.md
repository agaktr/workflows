# Create CRON job to deploy the dev branch

On SSH screen(2.2), run the following commands:
```bash
#On SSH screen(2.2) run the following command
crontab -e

#Add the following line to the file
#This will run the deploy script every 1 minute
* * * * * cd /home/{projectName} && git fetch && git checkout dev && git pull origin dev 
```

![Step 9](../images/step9.png)

<div align="right">
<a href="https://github.com/agaktr/workflows/blob/master/steps/step10.md" align="right">Next: Install Dependencies</a>
</div>  
