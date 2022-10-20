# Create database

```bash
#Create database if it doesn't exist (most likely it does)
php bin/console doctrine:database:create

#Create tables from the already made migrations
php bin/console doctrine:migrations:migrate

#Load fixtures with sample data (optional)
php bin/console doctrine:fixtures:load
```

<div align="right">
<a href="https://github.com/agaktr/workflows/blob/master/steps/step14.md" align="right">Next: Clear Cache</a>
</div>  
