# Application Packaging for Karaf
Karaf has the ability to load features and OSGi bundles either by dropping them in the deploy folder or by logging in to the Karaf shell and deploying them by a set of deploy commands.

![alt text](https://raw.githubusercontent.com/uppsala-university/common-integration/master/docs/common-integration-deployment.png "Common Integration components deployment")

Karaf will look for bundles and features referenced by a 'mvn:'-url in the local maven repository and in any additional repositories specified in $KARAF_HOME/etc/org.ops4j.pax.url.mvn.cfg.


## Configuration
Copy the property file `se.sunet.ati.integration.common.cfg` to $KARAF_HOME/etc/ and update with appropriate values.


## Build
    mvn install


## Deploy
In Karaf shell:

    repo-add mvn:se.sunet.ati.integration/common-integration-packaging-karaf/1.0.0-SNAPSHOT/xml/features
    feature:install common-logdb-datasource
    feature:install common-amq
