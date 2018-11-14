# Introduction
An example project for dockerize an application with WebLogic.

## How to use

1. Run **docker pull container-registry.oracle.com/middleware/weblogic:12.2.1.3-dev** to get weblogic base image. You should follow the instruction in Oracle website to create an account before pulling the image.
2. Run **docker-compose -f docker-compose.weblogic.base.yaml build** to build your private base image. You should change the image name in 1221-domain/Dockefile.
3. Run **docker-compose build** to build your application image.
4. Run **docker-compose up** to start demo application.
5. Visit demo application via http://localhost:7001/login.
6. (Optional) Visit WebLogic admin console via http://localhost:7001/console.

## Notes
1. 1221-domain folder is copied from Oracle Docker Images.
2. Currently(until 2018/11/14), you should replace PRODUCTION_MODE with DOM_PRODUCTION_MODE in 1221-domain/Dockerfile.
   Please refer to [this issue](https://github.com/oracle/docker-images/issues/1049) for more details.

## References

1. [Application for demo](https://github.com/hellokoding/registration-login-spring-hsql) 
2. [Oracle Docker Images](https://github.com/oracle/docker-images)
