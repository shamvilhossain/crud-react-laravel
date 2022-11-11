

## Setup for development
- `git clone git@gitlab.com:confidence-group/cghris-new.git`
- `cd cghris-new`
- To create new git local branch run - `git checkout -b your_name/master` - "your_name/master" will be the git branch name
- `git push --set-upstream origin your_name/master`

- `composer install`

- Make sure .env file, otherwise copy .env.example
- `php artisan key:generate`

- `npm install`
- `cd frontend`
- `npm install`
- `cd ..`
- `npm run dev`

- `php artisan jwt:secret`
- `php artisan storage:link`
- `php artisan migrate:fresh --seed`
- `php artisan serve`

- Watching for changes: Running `npm run dev` every time you make changes to file is inefficient. Hopefully there's command so your changes can be watched and get reflected accordingly. It's `npm run watch`

## Common Artisan Commands
- Create Controller with api Resource - `php artisan make:controller API/Employees/EmployeeController -r --api`

- Make Model with Migration file - `php artisan make:model Employees/FamilyDetail -m`

- Fresh migrate with database seeders - `php artisan migrate:fresh --seed`

- Inverse seed generator (iSeed) - `php artisan iseed my_table,another_table`

- Creating Jobs (Queue Schedule) - `php artisan make:job Attendance/EmpWiseAttnPolicyJob`
- Make mail inside app/Mail - `php artisan make:mail Attendance/EmpWiseAttnPolicyMail`
- Make import - `php artisan make:import Leave/MultiLayerApprovalImport`


# Git

## Git Fetch and Merge Instructions
- `git fetch`
- `git merge origin/branch_name`


## Git Pull Instructions
- `git pull origin master` Or `git pull origin remote_branch_name`


## Git Commit / Push Instructions
- `git status` Please make sure - you are not committing unnecessary files
- `git add .`
- `git commit -m "Write relevant message about work"`
- `git push` Or `git push origin branch_name`

# JWT Issue Resolve
- `php artisan key:generate`
- `php artisan jwt:secret`
- `php artisan cache:clear`
- `php artisan config:clear`


# Template Info
- We are using - Vuexy Admin Template
- Demo URL - https://pixinvent.com/demo/vuexy-vuejs-laravel-admin-template/demo-1
- Documentation URL - https://pixinvent.com/demo/vuexy-vuejs-admin-dashboard-template/documentation/
- Frequently usage - https://bootstrap-vue.org/


# Others
- `php artisan optimize:clear`

## keyConstraints Instructions
- `php artisan make:migration keyConstraints`


## Xampp DNS Setup
- go to `C:\xampp\apache\conf\extra` and add the following lines here on 'httpd-vhosts.conf'

```
<VirtualHost *:80>
 ServerName www.cghris-new.test
 ServerAlias cghris-new.test
 DocumentRoot C:/xampp/htdocs/cghris-new/public
</VirtualHost>
```

- Windows start menu >> Type/ Search for "Notepad" >> Right click >> Run as Administrator
- File >> Open >> and go to `C:\Windows\System32\drivers\etc`
- Show file type - All Files (*.*)
- Open "hosts"
- Add the line, save and close Notepad - `127.0.0.5      cghris-new.test`

- Restart Xampp

## Module Wise Migration Create

-`php artisan make:migration create_erec_employee_requisitions_table --path=database/migrations/Erecruitments`
Or

-`php artisan migrate --path=database/migrations/Erecruitments`

## Specific Migration run
-`php artisan migrate --path=/database/migrations/2021_04_22_130332_key_constraints.php`

## Run Specific - Artisan Console Commands
-`php artisan accessDevicePunch:everyTenMinutes`


## Drop All Tables & Migrate
-------------------------
-`php artisan migrate:fresh`

## Drop All Tables,Migrate & seed database
---------------------------------------
-`php artisan migrate:fresh --seed`

## Module Wise Drop All Tables,Migrate & seed database
---------------------------------------
-`php artisan migrate --path=database/migrations/Erecruitments --seed` It does not work properly - it run all Module Seeder files :(

## Module Wise Create table seeder
-------------------
-`php artisan make:seeder table_sidder_name --path=database/migrations/Erecruitments`

## Seed specific table seeder
--------------------------

-`php artisan db:seed --class=UnitTableSeeder`
Or
-`php artisan db:seed --class="Database\\Seeders\\Erecruitments\\SeederName"`

## Table PARTITION on existing table
--------------------------
-`y2025m01 is last partition`
-`ALTER TABLE leav_daywise_leave_takens REORGANIZE PARTITION y2025m01 INTO ( 
PARTITION y2025m01 VALUES LESS THAN ('2025-02-01'),   
PARTITION y2025m02 VALUES LESS THAN MAXVALUE);`

## IF composer is not work
-`copy the content of package-lock-backup.json file to package-lock.json`
-`again run npm install`

## Remote MySQL Connection, Firewal
- The MySQL configuration file should be in .\xampp\mysql\bin\my.ini. You need to find the bind-address parameter and change it to 0.0.0.0
- Firewall - Inbound Rules - Allow connections from other host by allowing TCP, Local Port e.g. 80, 443, 3306, 21