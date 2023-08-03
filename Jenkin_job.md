# Create Jenkins Job
### The job with the name of registration form has been created ,fetching code from this repo ,building using maven and deploying the artifacts on tomcat server.

1.Created a Maven project.

2.Provided the Git repository URL to fetch code.

3.Specified the branch to build from in the Git section.

4.Implemented Poll SCM, which triggers builds upon commits at regular intervals.

5.In the Build section, defined the path to the pom.xml file that includes project information, dependencies, and build process details.

6.Set goals to perform the build process: clean install.

7.After a successful build, the generated artifacts, typically in the form of .war files, need to be deployed to the Tomcat server.

8.In the Post-build actions, the location of .war files is specified using the pattern

``` -sh **/*.war.  ```

9.Credentials for the Tomcat server are provided. It's essential for the specified user to have the necessary permissions to deploy artifacts to the server.

10.The URL of the Tomcat server is specified.
