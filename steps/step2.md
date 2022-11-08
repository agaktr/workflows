# Clone Apto Library

Open the project folder in the terminal and run the following commands to clone symfony5.4 project:
```bash
#Clone the repo inside your project root folder
git clone https://github.com/agaktr/apto.symfony.base.git

#copy files from symfony5.4/public_html/symfony to your project root folder
cp -r apto.symfony.base/* .

#remove the symfony5.4 folder
rm -rf apto.symfony.base
#or if you are using Windows PowerShell (PHPStorm terminal)
Remove-Item -Recurse -Force apto.symfony.base
```

![Step 2](../images/step2.png)

<div align="right">
<a href="https://github.com/agaktr/workflows/blob/master/steps/step3.md" align="right">Next: Install Dependencies</a>
</div>  
