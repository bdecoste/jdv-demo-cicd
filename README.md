#JDV xPaaS Image All-In-One Example/Demo
This project, along with jdv-demo-app and jdv-demo-vdb, contains all of the source for an all-in-one example/demo for deploying a
web application in an EAP pod accessing data via a JDV pod. The JDV pod and deployed VDBs are backed by several datasources including postgresql, flat file, 
excel file, and webservice.

##Structure
This example/demo is divided into 4 roles:
 * Application Developer: Responsible for authoring the web application deployed in EAP (jdv-demo-app git repo)
 * VDB Developer: Responsible for authoring the VDB(s) deployted in JDV (jdv-demo-vdb git repo)
 * OpenShift DBA: Responsible for providing all of the artifacts (e.g. drivers, resource adapters, translators) and configuration for the available/applicable datasources for both
the application deployed in EAP and the VDBs deployed in JDV (jdv-demo/ose-dba git repo)
 * OpenShift Deployer: Responsible for deploying to OpenShift (jdv-demo/ose-cicd git repo)

##JDV Example

Create "demo" project

```
$ oc new-project demo
```

Deploy example/demo

```
$ oc process -f ose-cicd/datavirt63-demo-s2i.json | oc create -f -
```

Test application via http://datavirt-eap-demo.cloudapps.example.com/demo-webapp (hostname is environment specific so may need to be changed)
