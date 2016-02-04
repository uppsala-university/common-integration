Application Packaging for Karaf
===============================

Features XML for Application Packaging in Karaf:


Build
-----

    mvn install


Deploy
------

In Karaf shell:

    repo-add mvn:se.sunet.ati.integration/common-integration-packaging-karaf/1.0.0-SNAPSHOT/xml/features
    feature:install common-logdb-datasource
    feature:install common-amq
