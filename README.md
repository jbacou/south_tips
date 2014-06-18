south_tips
==========
====================================================================
Simple-as-possible instructions to add a field (or more) using South 
to an existing Django model with existing data.
====================================================================
 
Two versions:
  1. Super-condensed (the bare minimum - jfdi)
  2. Detailed-but-brief (if you want more information).
 
Notes:
  [appname] is a placeholder for the name of your Django app.
  South works separately on each application, not on a whole project.
  Commands are in backticks: `command here`
 
 
====================================================================
1. Super-condensed instructions:
   (you already know your way around, but are new to South)
 
`sudo easy_install South`
 
add 'south' to INSTALLED_APPS
`./manage.py syncdb`
`./manage.py convert_to_south [appname]`
 
add new field(s)
`./manage.py schemamigration [appname] --auto`
`./manage.py migrate [appname]`
 
see the new field in your Django project admin.
 
 
====================================================================
2. Detailed-but-brief instructions:
   (if you want more details)
 
1. get South with: `sudo easy_install South` (note capital 'S')
 
2. add 'south' to your project's INSTALLED_APPS in settings.py (note small 's')
  (test the install: `./manage.py shell` then `import south` - no message=good!)
 
3. type: `./manage.py syncdb`
  (make South migration-tracking tables)
 
4. type: `./manage.py convert_to_south [appname]`
  (shortcut for --initial followed by a migrate --fake)
 
5. add the field to your model
   - unless you pre-populate it with default data, it needs both
     null=True, blank=True
     to be empty in the database and for Django admin validation.
 
6. type: `./manage.py schemamigration [appname] --auto`
 
7. type: `./manage.py migrate [appname]`
 
8. You can now use the new field and view it in your Django admin.
