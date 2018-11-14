# Introduction
An example project for dockerize an application with WebLogic.

## How to use

### Before you begin
1. Run **docker pull container-registry.oracle.com/middleware/weblogic:12.2.1.3-dev** to get weblogic base image. You should follow the instruction in Oracle website to create an account before pulling the image.
2. Make sure docker-compose is avaliable in your dev box.

### Build and test application image for Dev Environment
1. Run **docker-compose -f docker-compose.weblogic.base.dev.yaml build** to build your private base image. (Please change the image name in the above yaml file.)
2. Run **docker-compose -f docker-compose.dev.yaml build** to build your application image.
3. Run **docker-compose -f docker-compose.dev.yaml up** to start demo application.
4. Fix any application issue, like ClassNotFound. Then rebuild your application image until your application is working properly.
5. Run **docker-compose -f docker-compose.dev.yaml down** to stop demo application.

### Build and test application image for Prod Environment
1. Run **docker-compose -f docker-compose.weblogic.base.prod.yaml build** to build your private base image for production.
2. Run **docker-compose -f docker-compose.prod.yaml build** to build your application image for production.
3. Run **docker-compose -f docker-compose.prod.yaml up** to start your application.
4. Open demo application via http://localhost:7001/login.
5. Open WebLogic admin console via http://localhost:7001/console with this credential (weblogic/welcome1).

## Notes
1. 1221-domain folder is copied from Oracle Docker Images.
2. The difference between *.dev.yaml and *.prod.yaml is the deploy method (auto-deploy v.s. wlst) and production mode.
3. Currently(until 2018/11/14), you should replace PRODUCTION_MODE with DOM_PRODUCTION_MODE in 1221-domain/Dockerfile.
   Please refer to [this issue](https://github.com/oracle/docker-images/issues/1049) for more details.

## Disclamier
**I am not a WebLogic expert, please feel free to file a pull request to fix any issue.**

## References
1. [Demo application: registration-login-spring-hsql](https://github.com/hellokoding/registration-login-spring-hsql) 
2. [Oracle Docker Images](https://github.com/oracle/docker-images)
