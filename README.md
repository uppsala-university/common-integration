# Common Integration
The integration concept is based on mediation of events, i.e. [messaging](http://www.enterpriseintegrationpatterns.com/patterns/messaging/Messaging.html). The events are mediated by [messaging channels](http://www.enterpriseintegrationpatterns.com/patterns/messaging/MessageChannel.html) implemented as message queues where the queues resist inside a [message broker](http://www.enterpriseintegrationpatterns.com/patterns/messaging/MessageBroker.html) instance.

The concept is also based on the principle that the same event should not be processed more than once. This is implemented by the [idem potent receiver](http://www.enterpriseintegrationpatterns.com/patterns/messaging/IdempotentReceiver.html) pattern from the [Enterprise Integration Patterns](http://www.eaipatterns.com). The implementation of this pattern needs persistent storage for beeing consistent throught system restarts. The persistent storage is implemented by a relational database management system.

Basically there are two common ServiceMix integration components that in some way are considered as part of the platform:

- RDBMS datasource as OSGi service
- JMS datasource as OSGi service

![alt text](https://raw.githubusercontent.com/uppsala-university/common-integration/master/docs/common-integration.png "Common Integration Components")

## RDBMS datasource
The RDBMS hosted by the integration runtime machine is a MariaDB and the datasource therefore is based on the MySQL driver. The datasource is published to the platform as an OSGi service. 

The configured datasource component is configured for beeing XA aware, i.e. register operations in a platform global transaction manager that handles transaction accross multiple resources. 

## JMS datasource
The JMS compatible message broker hosted by the integration runtime machine is a Apache ActiveMQ. The driver is a Apache Camel Active MQ component published to the platform as an OSGi service.

There are two broker instances configured in the runtime environment. The first broker is the main broker where the message queues resists. The configured component for this broker is XA aware, i.e. register operations in a platform global transaction manager that handles transactions accross multiple resources.

The second broker is a separate broker instance where dead letter queues resists. These queues should not be handled in the same transaction management system as the main queues since these should not be rolled back upon failure. Therefore the configured component for the dead letter broker is not configured for beeing XA aware.

## Deployment
Deployment is bound to the execution enviroment. For deployment in a Karaf/ServiceMix environment read the [Karaf deployment documentation](https://github.com/uppsala-university/common-integration/tree/master/common-integration-packaging-karaf).