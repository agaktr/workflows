# Create Webpack Assets

If we are on a development server (ex. blackflag.cloud), we need to change the `publicPath` in `webpack.config.js` file to use the correct path for the public folder.

```bash
#change webpack.config.js file to use the correct path for the public folder
#change the following line
publicPath: '/symfony/public/build',
#to
publicPath: '/build',
```

If instead we are using XAMPP, you can use the following configuration:
```bash
#change webpack.config.js file to use the correct path for the public folder
#change the following line
publicPath: '/symfony/public/build',
#to
publicPath: '/public/build',
```

In the terminal, run the following commands to build the assets:
```bash
#build assets
yarn encore dev
#or if you want to watch for changes
yarn encore dev --watch
```

![Step 4](../images/step4.png)

<div align="right">
<a href="https://github.com/agaktr/workflows/blob/master/steps/step4.md" align="right">Next: Install Dependencies</a>
</div>  
