Application Packaging for Karaf
===============================

Features XML for Application Packaging in Karaf:


Configuration
-------------

Copy the property file se.sunet.ati.integration.common.cfg to $KARAF_HOME/etc/ and update with appropriate values.


Build
-----

    mvn install


Deploy
------

In Karaf shell:

    repo-add mvn:se.sunet.ati.integration/common-integration-packaging-karaf/1.0.0-SNAPSHOT/xml/features
    feature:install common-logdb-datasource
    feature:install common-amq
