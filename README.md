# wildfly-websocket-war
sample war file

1) Download wildfly-16 from below link and unzip it:
https://download.jboss.org/wildfly/16.0.0.Final/wildfly-16.0.0.Final.zip

2) Install java 8

3) SET following environment variables in CMD
export JAVA_HOME=<PATH-TO-JAVA>
export PATH=$JAVA_HOME/bin:$PATH
export JBOSS_HOME=<WILDFLY-FOLDER-LOCATION>/wildfly-16.0.0.Final

4) copy wildfly-websocket.war file into "$JBOSS_HOME/standalone/deployments" folder

5) start the wildfly server as follows
=> $JBOSS_HOME/bin/standalone.sh

6) Application will be available at http://localhost:8080/myapp/

Issue:
- Once click on "Open connection" there is error in browser console as 404 and in server log there is following error
--------------------------------------------------------------
21:12:02,163 INFO  [io.undertow.servlet] (default task-4) 
ActionController::RoutingError (No route matches [GET] "/websocket/helloName"):
  gems/gems/actionpack-3.2.22/lib/action_dispatch/middleware/debug_exceptions.rb:21:in `call'
  gems/gems/actionpack-3.2.22/lib/action_dispatch/middleware/show_exceptions.rb:56:in `call'
  gems/gems/railties-3.2.22/lib/rails/rack/logger.rb:32:in `call_app'
  gems/gems/railties-3.2.22/lib/rails/rack/logger.rb:16:in `call'
  gems/gems/activesupport-3.2.22/lib/active_support/tagged_logging.rb:22:in `tagged'
  gems/gems/railties-3.2.22/lib/rails/rack/logger.rb:16:in `call'
  gems/gems/actionpack-3.2.22/lib/action_dispatch/middleware/request_id.rb:22:in `call'
  gems/gems/rack-1.4.7/lib/rack/methodoverride.rb:21:in `call'
  gems/gems/rack-1.4.7/lib/rack/runtime.rb:17:in `call'
  gems/gems/activesupport-3.2.22/lib/active_support/cache/strategy/local_cache.rb:72:in `call'
  gems/gems/rack-1.4.7/lib/rack/lock.rb:15:in `call'
  gems/gems/actionpack-3.2.22/lib/action_dispatch/middleware/static.rb:83:in `call'
  gems/gems/railties-3.2.22/lib/rails/engine.rb:484:in `call'
  gems/gems/railties-3.2.22/lib/rails/application.rb:231:in `call'
  classpath:/rack/handler/servlet.rb:22:in `call'
-------------------------------------------------------------------- 


Note:
In server log file the you can find websocket serverEndPoint is added as follows
=> Adding annotated server endpoint class org.jboss.as.quickstarts.websocket_hello.HelloName for path /websocket/helloName

Websocket endpoint is in lib/websocket-endpoint.jar there is only one annotated class, source code can be founnd at https://github.com/wildfly/quickstart/blob/16.0.0.Final/websocket-hello/src/main/java/org/jboss/as/quickstarts/websocket_hello/HelloName.java
