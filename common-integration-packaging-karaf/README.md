Application Packaging for Karaf
===============================

Features XML for Application Packaging in Karaf:


Build
-----

    mvn install


Deploy
------

In Karaf/Servicemix shell:

    features:addurl mvn:se.sunet.ati.integration/common-integration-packaging-karaf/1.0.0-SNAPSHOT/xml/features
    features:install common-logdb-datasource
    features:install common-amq
