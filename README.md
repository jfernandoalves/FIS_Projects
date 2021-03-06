# Spring-Boot CXF JAXWS QuickStart

This example demonstrates how you can use Apache CXF with Spring Boot
based on a [fabric8 Java base image](https://github.com/fabric8io/base-images#java-base-images).

The quickstart uses Spring Boot to configure a little application that includes a CXF JAXWS endpoint.


### Building

The example can be built with

    mvn clean install


### Running the example locally

The example can be run locally using the following Maven goal:

    mvn spring-boot:run


### Running the example in Kubernetes

It is assumed a running Kubernetes platform is already running. If not you can find details how to [get started](http://fabric8.io/guide/getStarted/index.html).

Assuming your current shell is connected to Kubernetes or OpenShift so that you can type a command like

```
kubectl get pods
```

or for OpenShift

```
oc get pods
```

Then the following command will package your app and run it on Kubernetes:

```
mvn fabric8:run
```

The output log will give the URL to access the endpoint, something like
```
[INFO] F8:[SVC] spring-boot-cxf-jaxws: http://192.168.64.7:32224
```

You need to append the context-path `service/hello` to access the service so the URL is something like

    http://192.168.64.7:32224/service/hello

To list all the running pods:

    oc get pods

Then find the name of the pod that runs this quickstart, and output the logs from the running pods with:

    oc logs <name of pod>

You can also use the [fabric8 developer console](http://fabric8.io/guide/console.html) to manage the running pods, and view logs and much more.

To access the endpoint, use the host and port from the output log when run mvn fabric8:run

    http://192.168.64.7:32224/service/hello?wsdl
    
... will now display the generated WSDL.


### Integration Testing

The example includes a [fabric8 arquillian](https://github.com/fabric8io/fabric8/tree/v2.2.170.redhat/components/fabric8-arquillian) OpenShift Integration Test. 
Once the container image has been built and deployed in OpenShift, the integration test can be run with:

    mvn test -Dtest=*KT

The test is disabled by default and has to be enabled using `-Dtest`. Open Source Community documentation at [Integration Testing](https://fabric8.io/guide/testing.html) and [Fabric8 Arquillian Extension](https://fabric8.io/guide/arquillian.html) provide more information on writing full fledged black box integration tests for OpenShift. 


### More details

You can find more details about running this [quickstart](http://fabric8.io/guide/quickstarts/running.html) on the website. This also includes instructions how to change the Docker image user and registry.

