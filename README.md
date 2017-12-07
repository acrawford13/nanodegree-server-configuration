# Linux Server Configuration Project

## Server Information
IP Address: 18.195.227.125  
SSH Port: 2200  
Application URL: [18.195.227.125/library](http://18.195.227.125/library)

## Packages Installed

- finger
- apache2
- libapache2-mod-wsgi
- pip
- virtualenv
- postgresql

## Configuration Changes

- Created user `grader`
- Added `grader` to group `sudo`
- Added rule to allow `grader` to use sudo commands without password
- Added authorization key for grader
- Prohibited remote login for `root`
- Changed ssh port to 2200
- Configured firewall to only allow connections on ports 80, 123 & 2200
- Added redirect from / to /library

## Third Party Resources

### General Reading

- [Introduction to pip and virtualenv](https://www.dabapps.com/blog/introduction-to-pip-and-virtualenv-python/)

### References
- [usermod](https://linux.die.net/man/8/usermod)
- [PostgreSQL Documentation](https://www.postgresql.org/docs/9.5/static/index.html)
- [Apache Module mod_alias](https://httpd.apache.org/docs/current/mod/mod_alias.html)

### Guides
- [Flask Documentation: Deploying](http://flask.pocoo.org/docs/0.10/deploying/mod_wsgi/)
- [Installing packages using pip and virtualenv](https://packaging.python.org/guides/installing-using-pip-and-virtualenv/)
- [Problems with the Digital Ocean Tutorial](https://discussions.udacity.com/t/problems-with-the-digital-ocean-tutorial/336376)
- [How To Deploy a Flask Application on an Ubuntu VPS](https://www.digitalocean.com/community/tutorials/how-to-deploy-a-flask-application-on-an-ubuntu-vps)

### Troubleshooting
- **Issue:** My app wasn't finding files like 'google_client_secret.json'. The problem could have been fixed by using an absolute path but I wanted to find a more flexible solution.
- **Solution:** Store the project root in a variable in the application: `PROJECT_ROOT = os.path.realpath(os.path.dirname(__file__))`
- **Resources:**
    - [Stack Overflow: WSGI can't find file in same directory in app](https://stackoverflow.com/questions/44742566/wsgi-cant-find-file-in-same-directory-in-app)
    - [mod_wsgi: Application Issues - Application Working Directory](http://modwsgi.readthedocs.io/en/develop/user-guides/application-issues.html#application-working-directory)
----
- **Issue:** I had successfully installed a package in the virtual environment once, but when I tried to install subsequent packages they were being installed in the user's home directory instead.
- **Solution:** I realised I had renamed my application folder since initialising my virtual environment, so I had to update my `bin/activate` and `bin/pip` files with the new name
- **Resource:** [VirtualEnv/Pip trying to install packages globally](https://stackoverflow.com/questions/20942982/virtualenv-pip-trying-to-install-packages-globally)
