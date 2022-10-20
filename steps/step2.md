# Clone Apto Library

Open the project folder in the terminal and run the following commands to clone symfony5.4 project:
```bash
#Clone the repo inside your project root folder
git clone https://github.com/agaktr/symfony5.4.git

#copy files from symfony5.4/public_html/symfony to your project root folder
cp -r symfony5.4/public_html/symfony/* .

#remove the symfony5.4 folder
rm -rf symfony5.4
#or if you are using Windows PowerShell (PHPStorm terminal)
Remove-Item -Recurse -Force symfony5.4
```

![Step 2](../images/step2.png)

<div align="right">
<a href="https://github.com/agaktr/workflows/blob/master/steps/step3.md" align="right">Next: Install Dependencies</a>
</div>  
