#  Engaging Spring Cloud Sleuth with Spring Boot Microservices

ch13/sample01

p.377 ~ p.380

p.379
```
\> mvn clean install
\> mvn spring-boot:run
\> curl http://localhost:9000/order/11
```

#  Tracing Messages Between Multiple Microservices with Spring Cloud Sleuth

p.380 ~ p.386


ch13/sample02
```
\> mvn clean install
\> mvn spring-boot:run

\> curl -v  -k  -H "Content-Type: application/json"   \
-d '{"customer_id":"101021","payment_method":{"card_type":"VISA","expiration":"01/22","name":"John Doe","billing_address":"201, 1st Street, San Jose, CA"},"items":[{"code":"101","qty":1},{"code":"103","qty":5}],"shipping_address":"201, 1st Street, San Jose, CA"}'   \
http://localhost:9000/order


```