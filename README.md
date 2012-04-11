# Getting started with WAR deployment on Heroku

## Pre requisites

You will require the following:

* [Heroku toolbelt](https://toolbelt.heroku.com/)
* [Heroku account](http://www.heroku.com/signup)

Additionally your heroku account needs to be enabled for WAR deployments. Email us at anand@heroku.com if you need your account enabled for WAR deployment.

## Getting started

### 1. Install the <code>heroku-deploy</code> CLI plugin

Use the following command to install the <code>heroku-deploy</code> plugin:

    ### Git URL needs to be finalized
    heroku plugins:install https://github.com/heroku/heroku-deploy

### 2. Create a Heroku application

Use the following command to create a new application on Heroku

    heroku create --stack cedar 

In case you want to use a different name instead of the generated application name use the following command:

    heroku rename <new_name> --app <generated_name>

### 3. Create a WAR file

You can use any method to generate a WAR file. You can use <code>maven</code>,<code>ant</code> or simply export your application from your IDE as a WAR file. 

The only requirement is that the WAR file is a standard Java web application and adheres to the standard web application structure and conventions.

### 4. Deploy your WAR 

In order to deploy your WAR use the following command:

    heroku deploy:war --app <app_name> <absolute_path_to_war_file>

If you are in an application directory, use the following command:

    heroku deploy:war <absolute_path_to_war_file>

## Frequently asked questions

### What container does my WAR file deploy to?

Your WAR file will be deployed to Tomcat 7 using the the [webapp-runner]()

### What types of WAR files can I deploy?

You should be able to deploy any WAR file as long as it conforms to the standard Java web application conventions. The application should also follow best practices for web applications on Heroku such as stateless applications, using Environment variables, no file based acccess etc.

### Is there a file size limit on my WAR ?

Yes. You can only deploy WAR files <b><u>less than 100MB</u></b>

### Do I need a <code>Procfile</code>

To deploy just a WAR file to your application, you do not need to include a <code>Procfile</code>

### Can I deploy a WAR to an existing application ?

Yes. The WAR deployment will create a new release with the Procfile containing just your web application. The process will not update an existing <code>Procfile</code>. If you need to revert back to an earlier release use <code>heroku rollback</code>.