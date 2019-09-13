ticket-monster: Assortment of technologies including Arquillian
========================
TicketMonster is an online ticketing demo application that gets you started with JBoss technologies, and helps you learn and evaluate them.

Author: Gal Levinshtein - Modified to use Angular with RedHat Jboss EAP 7.0 
Level: Intermediate
Technologies: CDI, Angular, JPA, EJB, JPA, Hibernate, JAX-RS, BV
Summary: An example that incorporates multiple technologies
Target Project: RedHat Jboss EAP 7.0
Source: <https://access.redhat.com/products/red-hat-jboss-enterprise-application-platform>

What is it?
-----------

This is your project! It is a sample, deployable Maven 3 project to help you get your foot in the door developing with Java EE 8 on RedHat Jboss EAP 7.0 technologies, and helps you learn and evaluate them.

I also suggest using either Intellij Webstorm or Visual Source Code with John Papa's snipplets for converting the Angular code to angular 4 using the CLI.  This is outside the scope of this tutorial.

This project is setup to allow you to create a compliant Java EE 8 application using Angular 2, CDI 1.1, EJB 3.3, JPA 2.1 and Bean Validation 1.1. It includes a persistence unit and some sample persistence and transaction code to introduce you to database access in enterprise Java.

There is a longer tutorial for this quickstart in the [Getting Started Developing Applications Guide] (https://developers.redhat.com/ticket-monster/?referrer=jbd) which I also compiled to a PDF for easy follow easily.

System requirements
-------------------

All you need to build this project is Java 8.0 (Java SDK 1.8) or better, Maven 3.1 or better.

The application this project produces is designed to be run on RedHat Jboss EAP 7.0.

 
Configure Maven
---------------

If you have not yet done so, you must [Configure Maven](https://github.com/jboss-developer/jboss-developer-shared-resources/blob/master/guides/CONFIGURE_MAVEN.md) before testing the quickstarts.


Start JBoss EAP with the Web Profile
-------------------------

1. Open a command line and navigate to the root of the JBoss server directory.
2. The following shows the command line to start the server with the web profile:

        For Linux:   JBOSS_HOME/bin/standalone.sh
        For Windows: JBOSS_HOME\bin\standalone.bat

 
Build and Deploy the Quickstart
-------------------------

_NOTE: The following build command assumes you have configured your Maven user settings. If you have not, you must include Maven setting arguments on the command line. See [Build and Deploy the Quickstarts](https://github.com/jboss-developer/jboss-eap-quickstarts#build-and-deploy-the-quickstarts) for complete instructions and additional options._

1. Make sure you have started the JBoss Server as described above.
2. Open a command line and navigate to the root directory of this quickstart.
3. Type this command to build and deploy the archive:

        build clean package jboss-as:deploy

4. This will deploy `target/ticket-monster.war` to the running instance of the server.
 

Access the application 
---------------------

The application will be running at the following URL: <http://localhost:8080/ticket-monster/>.


Undeploy the Archive
--------------------

1. Make sure you have started the JBoss Server as described above.
2. Open a command line and navigate to the root directory of this quickstart.
3. When you are finished testing, type this command to undeploy the archive:

        mvn jboss-as:undeploy


Run the Arquillian Tests 
-------------------------

This quickstart provides Arquillian tests. By default, these tests are configured to be skipped as Arquillian tests require the use of a container. 

_NOTE: The following commands assume you have configured your Maven user settings. If you have not, you must include Maven setting arguments on the command line. See [Run the Arquillian Tests](https://github.com/jboss-developer/jboss-developer-shared-resources/blob/master/guides/RUN_ARQUILLIAN_TESTS.md) for complete instructions and additional options._

1. Make sure you have started the JBoss Server as described above.
2. Open a command line and navigate to the root directory of this quickstart.
3. Type the following command to run the test goal with the following profile activated:

        mvn clean test -Parq-wildfly-remote


Run the Quickstart in JBoss Developer Studio or Eclipse
-------------------------------------
You can also start the server and deploy the quickstarts from Eclipse using JBoss tools. For more information, see [Use JBoss Developer Studio or Eclipse to Run the Quickstarts](https://github.com/jboss-developer/jboss-developer-shared-resources/blob/master/guides/USE_JBDS.md) 

Generating the administration site
-------------------------------------

_NOTE: This step is optional. The administration site is already present in the source code. If you want to regenerate it from Forge, and apply the changes outlined in the tutorial, you may continue to follow the steps outlined here. Otherwise, you can skip this step and proceed to build TicketMonster._

Before building and running TicketMonster, you must generate the administration site with Forge.

1. Ensure that you have [JBoss Forge](http://jboss.org/forge) installed. The current version of TicketMonster supports version 2.6.0.Final or higher of JBoss Forge. JBoss Developer Studio 8 is recommended, since it contains JBoss Forge 2 with all the necessary plugins for the TicketMonster app.

2. Start the JBoss Forge console in JBoss Developer Studio. This can be done from the Forge Console view. If the view is not already visible, it can be opened through the 'Window' menu: _Window_ -> _Show View_ -> _Other..._. Select the 'Forge Console' item in the dialog to open the Forge Console. Click the _Start_ button in the Forge Console tab, to start Forge. 

3. From the JBoss Forge prompt, browse to the 'demo' directory of the TicketMonster sources and execute the script for generating the administration site
    
	    $ cd ticket-monster/demo
	    $ run admin_layer.fsh

    The git patches need to be applied manually. Both the patches are located in the patches sub-directory. To apply the manual changes, first apply the patch located in file _admin_layer_functional.patch_. Then perform the same for the file _admin_layer_graphics.patch_ if you want to apply the style changes for the generated administration site. You can do so in JBoss Developer Studio, by opening the context-menu on the project (Right-click on the project) and then apply a git patch via _Team_ -> _Apply Patch..._. Locate the patch file in the Workspace, select it and click the 'Next' button. In the next dialog, select to apply the patch on the 'ticket-monster' project in the workspace. Click Finish in the final page of the wizard after satisfying that the patch applies cleanly.

4. Deployment to JBoss EAP 6.3 is optional. The project can be built and deployed to a running instance of JBoss EAP through the following command in JBoss Forge:

	    $ build clean package jboss-as:deploy


Debug the Application
------------------------------------

If you want to debug the source code or look at the Javadocs of any library in the project, run either of the following commands to pull them into your local repository. The IDE should then detect them.

    mvn dependency:sources
    mvn dependency:resolve -Dclassifier=javadoc
    
Building TicketMonster
------------------------------------

TicketMonster can be built from Maven, by runnning the following Maven command:

    mvn clean package
	
Building TicketMonster with tests
------------------------------------
	
If you want to run the Arquillian tests as part of the build, you can enable one of the two available Arquillian profiles.

For running the tests in an _already running_ application server instance, use the `arq-jbossas-remote` profile.

    mvn clean package -Parq-jbossas-remote

If you want the test runner to _start_ an application server instance, use the `arq-jbossas-managed` profile. You must set up the `JBOSS_HOME` property to point to the server location, or update the `src/main/test/resources/arquillian.xml` file.

    mvn clean package -Parq-jbossas-managed
	
Building TicketMonster with Postgresql (for OpenShift)
------------------------------------

If you intend to deploy into [OpenShift](http://openshift.com), you can use the `postgresql-openshift` profile

    mvn clean package -Ppostgresql-openshift

### Building TicketMonster with MySQL (for OpenShift)

If you intend to deploy into [OpenShift](http://openshift.com), you can use the `mysql-openshift` profile

    mvn clean package -Pmysql-openshift
	
Running TicketMonster
------------------------------------

You can run TicketMonster into a local JBoss EAP 6.3 instance or on OpenShift.

Running TicketMonster locally
------------------------------------

#### Start JBoss Enterprise Application Platform 7

1. Open a command line and navigate to the root of the JBoss server directory.
2. The following shows the command line to start the server with the web profile:

        For Linux:   JBOSS_HOME/bin/standalone.sh
        For Windows: JBOSS_HOME\bin\standalone.bat
		
#### Deploy TicketMonster

1. Make sure you have started the JBoss Server as described above.
2. Type this command to build and deploy the archive into a running server instance.

        mvn clean package jboss-as:deploy
	
	(You can use the `arq-jbossas-remote` profile for running tests as well)

3. This will deploy `target/ticket-monster.war` to the running instance of the server.
4. Now you can see the application running at `http://localhost:8080/ticket-monster`

### Running TicketMonster in OpenShift

#### Create an OpenShift project

> The following variables are used in these instructions. Be sure to replace them as follows:
* APP_NAME should be replaced with the name of the application you create on OpenShift.
* YOUR_DOMAIN_NAME should be replaced with the OpenShift domain name.
* APPLICATION_UUID should be replaced with the UUID generated by OpenShift for your application, for example: 52864af85973ca430200006f
* TICKETMONSTER_MAVEN_PROJECT_ROOT is the location of the Maven project sources for the TicketMonster application.

1. Open a shell command prompt and change to a directory of your choice. Enter the following command to create a JBoss EAP 6 application:

        rhc app create -a APP_NAME -t jbosseap-6

   This command creates an OpenShift application named APP_NAME and will run the application inside the jbosseap-6 container. You should see some output similar to the following:

        Application Options
        -------------------
        Domain:     YOUR_DOMAIN
        Cartridges: jbosseap-6 (addtl. costs may apply)
        Gear Size:  default
        Scaling:    no
        
        Creating application 'APP_NAME' ... done
        
        
        Waiting for your DNS name to be available ... done
        
        Cloning into 'APP_NAME'...
        Warning: Permanently added the RSA host key for IP address '54.90.10.115' to the list of known hosts.
        
        Your application 'APP_NAME' is now available.
        
          URL:        http://APP_NAME-YOUR_DOMAIN.rhcloud.com/
          SSH to:     APPLICATION_UUID@APP_NAME-YOURDOMAIN.rhcloud.com
          Git remote: ssh://APPLICATION_UUID@APP_NAME-YOUR_DOMAIN.rhcloud.com/~/git/APP_NAME.git/
          Cloned to:  /Users/vineet/openshiftapps/APP_NAME
        
        Run 'rhc show-app APP_NAME' for more details about your app.

2. The create command creates a git repository in the current directory with the same name as the application.

   You do not need the generated default application, so navigate to the new git repository directory created by the OpenShift command and tell git to remove the source and pom files:

        cd APP_NAME
        git rm -r src pom.xml

3. Copy the TicketMonster application sources into this new git repository:

        cp -r TICKETMONSTER_MAVEN_PROJECT_ROOT/src .
        cp -r TICKETMONSTER_MAVEN_PROJECT_ROOT/pom.xml .

#### Use MySQL as the database

1. Add the MySQL 5.5 cartridge to the `ticketmonster` application:

        rhc cartridge add mysql-5.5 -a ticketmonster

2. Configure the OpenShift build process, to use the `mysql-openshift` profile within the project POM. To do so, create a file named `pre_build_jbosseap` under the `.openshift/action_hooks` directory located in the git repository of the OpenShift application, with the following contents:

        export MAVEN_ARGS="clean package -Popenshift,mysql-openshift -DskipTests"

3. Set the executable bit for the action hook:

        chmod +x TICKET_MONSTER_OPENSHIFT_GIT_REPO/.openshift/build_hooks/pre_build_jbosseap

   On Windows, you will need to run the following command to set the executable bit to the `pre_build_jbosseap` file:

        git update-index --chmod=+x .openshift/build_hooks/pre_build_jbosseap

#### Use PostgreSQL as the database

1. Add the PostgreSQL 9.2 cartridge to the `ticketmonster` application:

        rhc cartridge add postgresql-9.2 -a ticketmonster

2. Configure the OpenShift build process, to use the `postgresql-openshift` profile within the project POM. To do so, create a file named `pre_build_jbosseap` under the `.openshift/action_hooks` directory located in the git repository of the OpenShift application, with the following contents:

        export MAVEN_ARGS="clean package -Popenshift,postgresql-openshift -DskipTests"

3. Set the executable bit for the action hook:

        chmod +x TICKET_MONSTER_OPENSHIFT_GIT_REPO/.openshift/build_hooks/pre_build_jbosseap

   On Windows, you will need to run the following command to set the executable bit to the `pre_build_jbosseap` file:

        git update-index --chmod=+x .openshift/build_hooks/pre_build_jbosseap

#### Deploying to OpenShift

1. You can now deploy the changes to your OpenShift application using git as follows:

        git add -A
        git commit -m "TicketMonster on OpenShift"
        git push

   The final push command triggers the OpenShift infrastructure to build and deploy the changes.

   Note that the `openshift` profile in pom.xml is activated by OpenShift, and causes the WAR build by OpenShift to be copied to the deployments/ directory, and deployed without a context path.

   Now you can see the application running at http://APP_NAME-YOUR_DOMAIN.rhcloud.com/.

