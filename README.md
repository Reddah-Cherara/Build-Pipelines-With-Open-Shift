# Build-Pipelines-with-Open-Shift-
Sample to Build Pipelines with Open-Shift 

# Create Build Pipelines with Open-Shift 


## Setup project and jenkins


    oc new-project dev
    oc new-project qa
    oc new-project ci-cd
    oc new-app jenkins-ephemeral -n ci-cd


1. MBP-de-REDDAH:~ rcherara$ oc new-project rcherara-dev
Now using project "rcherara-dev" on server "https://127.0.0.1:8443".

You can add applications to this project with the 'new-app' command. For example, try:

    oc new-app centos/ruby-22-centos7~https://github.com/openshift/ruby-ex.git

to build a new example application in Ruby.
MBP-de-REDDAH:~ rcherara$ oc new-project rcherara-qa
Now using project "rcherara-qa" on server "https://127.0.0.1:8443".

You can add applications to this project with the 'new-app' command. For example, try:

    oc new-app centos/ruby-22-centos7~https://github.com/openshift/ruby-ex.git

to build a new example application in Ruby.

2. MBP-de-REDDAH:~ rcherara$ oc new-project rcherara-cicd-ms
Now using project "rcherara-cicd-ms" on server "https://127.0.0.1:8443".

You can add applications to this project with the 'new-app' command. For example, try:

    oc new-app centos/ruby-22-centos7~https://github.com/openshift/ruby-ex.git

to build a new example application in Ruby.

3. MBP-de-REDDAH:~ rcherara$ oc new-app jenkins-ephemeral -n rcherara-cicd-ms
--> Deploying template "openshift/jenkins-ephemeral" to project rcherara-cicd-ms

     Jenkins (Ephemeral)
     ---------
     Jenkins service, without persistent storage.
     
     WARNING: Any data stored will be lost upon pod destruction. Only use this template for testing.

     A Jenkins service has been created in your project.  Log into Jenkins with your OpenShift account.  The tutorial at https://github.com/openshift/origin/blob/master/examples/jenkins/README.md contains more information about using this template.

     * With parameters:
        * Jenkins Service Name=jenkins
        * Jenkins JNLP Service Name=jenkins-jnlp
        * Enable OAuth in Jenkins=true
        * Memory Limit=512Mi
        * Jenkins ImageStream Namespace=openshift
        * Disable memory intensive administrative monitors=false
        * Jenkins ImageStreamTag=jenkins:2

--> Creating resources ...
    route "jenkins" created
    deploymentconfig "jenkins" created
    serviceaccount "jenkins" created
    rolebinding "jenkins_edit" created
    service "jenkins-jnlp" created
    service "jenkins" created
--> Success
    Access your application via route 'jenkins-rcherara-cicd-ms.127.0.0.1.nip.io' 
    Run 'oc status' to view your app.

    
    
## create an example for which you want to setup pipeline   


oc new-app https://github.com/Reddah-Cherara/Spring-Boot-Rest-API-Example.git --name=HelloWorld -n rcherara-dev

