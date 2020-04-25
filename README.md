#!/bin/bash

echo "$1”

#creating a folder
file="task”
if  [ -d "$file" ] 
then
         echo "$file exists."
   
         rm -rf $file
else
         echo "$file not found."
fi

mkdir task

cd task

#cloning the repository

git clone "$1"


#function to check currently working branch

function git.branch {
  br=`git branch | grep "*"`
  echo ${br/* /}
}
git.branch

#creating configuration files in directory
 
cd `ls -d */`

touch sonar-project.properties

i1=sonar.projectKey=puppeteer
i2=sonar.projectKey=puppeteer
i3=sonar.projectVersion=1.0
i4=sonar.sources=.

i1=$i1
i2=$i2
i3=$i3
i4=$i4

echo "$i1" >> /opt/task/puppeteer/sonar-project.properties
echo "$i2" >> /opt/task/puppeteer/sonar-project.properties
echo "$i3" >> /opt/task/puppeteer/sonar-project.properties
echo "$i4" >> /opt/task/puppeteer/sonar-project.properties

#run sonar-scanner
/opt/sonar-scanner-4.2.0.1873-linux/bin/sonar-scanner

if [build successful]
then
       return 0
else
       return 1
fi
