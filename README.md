Shop project deployment steps
I. Environment Preparation
(1) Download and install VmwarePro virtual machine, VMware 17 download installation and activation
(2) Vmware install ubuntu virtual machine
(3) ubuntu installation and configuration of Java 8
(4) ubuntu installation configuration tomcat
(5) ubuntu installation configuration mysql detailed (root user password must be consistent with the code jdbc.properties):
https://www.sjkjc.com/mysql/install-on-ubuntu/
(6) ubuntu installation and configuration of redis(without remote connection)

Second, the project packaging
(1) in the local project into shop.war file
In the local Idea environment, click on the right side of the maven button in the package, at this time will generate the target directory, the following shop.war file, which is a complete and runnable project files, including the front-end, back-end and dependencies.
Need to ensure that the project can run properly before the war file will be generated.
(2) Go to the mysql database under the root user and execute source . /schema.sql file to create the shop database and related tables; execute source . /dbdata.sql file to import the data.
(3) Transfer the packaged war file to the webapps of tomcat in ubuntu virtual machine.
(4) You need to modify the server.xml file under conf in the tomcat directory and add it in Host:
     <Context docBase=“shop” path=“/” reloadable=“false” />
Modify it:
If you don't modify it, it will cause the path of shop project to be loaded incorrectly, which is manifested as no effect of CSS file.
(5) cd to the bin directory of tomcat, run sh startup.sh to start tomcat.(sh shutdown.sh is to shut down tomcat)
(6) Visit your browser 127.0.0.1:8080/shop/
