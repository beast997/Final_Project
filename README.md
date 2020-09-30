# Final_Project

###### NOTE: Locally, you must Install nodejs and run main.js in /Communication/node/main.js for the Communication Application to work; also adjust the 2 absolute paths in the main.js file to match the directory structure

### LOCAL INSTALLATION (Windows Systems)
###### to use linux style commands of this README Please Install git bash (http://www.geekgumbo.com/2010/04/09/installing-git-on-windows/)
##### Create a Directory in your drive C:
##### 
mkdir /c/g1
##### 
mkdir /c/g1/database
##### 
mkdir /c/g1/source
##### 
mdkir /c/g1/virtualenv
##### 
mkdir /c/g1/static

##### Clone Project into source folder
git Clone https://github.com/CS673S15-Group1/Final_Project /c/g1/source

##### Create a Virtual Environment
###### NOTE: must have Installed python 2.7 to the default directory in C:\Python27
###### NOTE: must have Virtual env Installed 'pip install virtualenv' -- must have pip Installed, usually included on windows system installs
virtualenv -p /c/Python27/python.exe /c/g1/virtualenv

##### Change directory to the project source
cd /c/g1/source/group1

##### Install dependencies 
###### NOTE: windependencies file for windows since readline is not compatible, may have to change all 'import readline' to 'import pyreadline as readline'
../../virtualenv/Scripts/pip.exe install -r ../windependencies.txt

##### make the migration files
../../virtualenv/Scripts/python.exe manage.py makemigrations

##### Run the database migration
../../virtualenv/Scripts/python.exe manage.py migrate

##### Run server, navigate to http://localhost:8000 in a browser
../../virtualenv/Scripts/python.exe manage.py runserver


### LOCAL INSTALLATION (*nix systems [Mac, Ubuntu...])
##### Create a directory in your home directory
##### 
mkdir ~/g1
##### 
mkdir ~/g1/database
##### 
mkdir ~/g1/source
##### 
mkdir ~/g1/virtualenv
##### 
mkdir ~/g1/static
##### Clone project into source folder
git Clone https://github.com/CS673S15-Group1/Final_Project ~/g1/source

##### Create a Virtual Environment
###### NOTE: must have installed python 2.7 to the default directory in /usr/local/bin with a python2.7 executable via altinstall
###### NOTE: must have virtual env installed 'pip install virtualenv' -- must have pip installed, usually included on windows system installs
###### NOTE: see server installation script under deploy_tools for details on installing a new python
virtualenv -p /usr/local/bin/python2.7 ~/g1/virtualenv

##### Change directory to the project source
cd ~/g1/source/group1

##### Install dependencies
../../virtualenv/bin/pip install -r ../dependencies.txt

##### Make the migration files
../../virtualenv/bin/python manage.py makemigrations

##### Run the database migration
../../virtualenv/bin/python manage.py migrate

##### Run server, navigate to http://localhost:8000 in a browser
../../virtualenv/bin/python manage.py runserver


### SERVER INSTALLATION (*nix systems)
###### NOTE: Follow the commands under deploy_tools serverInstallcommands.sh (not tested as an executable shell script)
###### NOTE: Must have fabric installed (on windows this will require a manual installation (setup_py) of pycrypto first, you may find pre-compiled windows binaries Here (http://www.voidspace.org.uk/python/modules.shtml#pycrypto)
##### Change directory to where deploy_tools is on your local computer - this script is deployed from your local computer to the server
cd /c/g1/source/deploy_tools
###### NOTE: Must Activate virtualenv with fabric (you may have fabric installed on your path python, and not require a virtualenv)
##### Run the fabfile.py script with the following command to upload the project from origin/master to the specified server
fab deploy:host=pgmvt@dev.3blueprints.com
