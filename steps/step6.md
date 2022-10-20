# Setup the Dev server

Login to the server and create a new virtual server: https://blackflag.cloud:10000/

```bash

Virtualmin > Create Virtual Server

#On the page, fill in the following fields:
Domain name: {projectName}.blackflag.cloud
Administration password: {password}
Server configuration template: symfony

#On Enable features check:
Setup Apache SSL website

#After, click on 
Create Server
```

![Step 6](../images/step6.png)

<div align="right">
<a href="https://github.com/agaktr/workflows/blob/master/steps/step7.md" align="right">Next: Login to the server via SSH from PHPStorm</a>
</div>  
