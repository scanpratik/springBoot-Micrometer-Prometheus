## Step 1: In pom.xml, add the dependency for micrometer-core and micrometer-prometheus-registry by adding following snippet.xml

<!-- Spring boot actuator to expose metrics endpoint -->
* <dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-actuator</artifactId>
</dependency>
<!-- Micormeter core dependecy  -->
* <dependency>
    <groupId>io.micrometer</groupId>
    <artifactId>micrometer-core</artifactId>
</dependency>
<!-- Micrometer Prometheus registry  -->
* <dependency>
    <groupId>io.micrometer</groupId>
    <artifactId>micrometer-registry-prometheus</artifactId>
</dependency>

## Step 2: add in application.properties: it will enable the actuator and Prometheus endpoints to be exposed by adding below properties.proper


* #Metrics related configurations
* management.endpoint.metrics.enabled=true
* management.endpoints.web.exposure.include=*
* management.endpoint.prometheus.enabled=true
* management.metrics.export.prometheus.enabled=true

## That is all you need to do to enable the metrics. Start the application with these changes and if you browse URL http://localhost:9000/actuator you should see the actuator endpoints.

Notice spring-boot 2 and actuator has enabled an endpoint http://localhost:9000/actuator/prometheus for us. If you browse this URL, you will be able to see the metrics exported from the person-application. The data is the actual metrics collected from the application and exported as JSON.
