# Deploy iApp from TMSH



Copied from : [Deploy an Application Service from an iApp Template via TMSH](https://devcentral.f5.com/s/question/0D51T00006i7QWZSA2/deploy-an-application-service-from-an-iapp-template-via-tmsh)

I've seen a couple of refernces to how to do this but nothing fully fledged out so here is my attempt to do so.
The actual man page of the command can be viewed by issuing the following from within TMSH.

```
help /sys application service
```

First off deploying an iApp from TMSH is not like deploying it from the GUI.
It is not interactive.
So all of the questions that the template wizard will ask you need to be answered at once.
The 'iApp' itself is actually a few different components which I won't go into great detail on because it's explained much better in other places.
One of these components however is a script that is executed once you are done filling out the wizard and hit 'Finished.'
The answers that you provided in the GUI are passed to the script as variables and then the script executes.
Deploying an iApp with TMSH essentially starts at this point.

So in order to deploy an iApp you have to figure out the variables to pass and their values.
The simplest way to do this is to deploy it through the GUI and then view it via TMSH with the list command.

```
list /sys application service testAppToDeploy.app/testAppToDeploy
````

As you can see the App gets it's own directory (testAppToDeploy.app/) and then you reference the name within it (testAppToDeploy) so I recommend using tab completion to discover the actual app name.

The output should look something like this.

```
sys application service testAppToDeploy.app/testAppToDeploy {
 description none
 device-group somegroup
 inherited-devicegroup true
 inherited-traffic-group true
 lists none
 metadata none
 partition Common
 strict-updates enabled
 tables {
  basic__snatpool_members {
   column-names none
   rows none
  }
  optimizations__hosts {
   column-names none
   rows none
  }
  server_pools__servers {
   column-names { port connection_limit addr }
   rows {
    {
     row { 80 0 10.1.1.1 }
    }
    {
     row { 80 0 10.1.1.2 }
    }
   }
  }
 }
 template f5.http
 template-modified no
 template-prerequisite-errors none
 traffic-group traffic-group-1
 variables {
  basic__addr {
   value 192.168.200.9
  }
  basic__create_redir {
   value Yes
  }
  basic__need_snatpool {
   value No
  }
  basic__redir_port {
   value 80
  }
  basic__secure_port {
   value 443
  }
  basic__snat {
   value No
  }
  basic__using_ntlm {
   value No
  }
  optimizations__lan_or_wan {
   value WAN
  }
  server_pools__create_new_monitor {
   value "Create New Monitor"
  }
  server_pools__create_new_pool {
   value "Create New Pool"
  }
  server_pools__lb_method_choice {
   value least-connections-member
  }
  server_pools__monitor_http_version {
   value "Version 1.0"
  }
  server_pools__monitor_interval {
   value 30
  }
  server_pools__monitor_recv {
   value OK
  }
  server_pools__monitor_send {
   value "GET /"
  }
  server_pools__tcp_request_queuing_enable_question {
   value No
  }
  ssl_encryption_questions__cert {
   value /Common/CopyOfDefault.crt
  }
  ssl_encryption_questions__key {
   value /Common/CopyOfDefault.key
  }
  ssl_encryption_questions__offload_ssl {
   value Yes
  }
 }
}
```

The parts you need to pay the most attention to are `variables`, `tables` and `lists`.
For this App we have only Tables and Variables so I'm going to take those sections and copy them somewhere else and modify the settings for my new deployment.
You will also need to add the verb `add`, `modify` or `replace-all-with` before the first parenthesis.
Also if you're pasting this into TMSH shell mode don't forget to remove all your newlines so that the comand becomes a single line.
So for this example tables becomes:

```
tables add { basic__snatpool_members { column-names none rows none } optimizations__hosts { column-names none rows none } server_pools__servers { column-names { port connection_limit addr } rows { { row { 80 0 10.1.1.1 } } { row { 80 0 10.1.1.2 } } } } }
```

Then just tack these modified sections on to the `create` command with any other options specified.
In the end you should have something that looks roughly like this.

```
create /sys application service aNewApplicationServiceName template f5.http description "This is my description" tables add { basic__snatpool_members { column-names none rows none } optimizations__hosts { column-names none rows none } server_pools__servers { column-names { port connection_limit addr } rows { { row { 80 0 10.1.1.1 } } { row { 80 0 10.1.1.2 } } } } } variables add { basic__addr { value 192.168.200.11 } basic__create_redir { value Yes } basic__need_snatpool { value No } basic__redir_port { value 80 } basic__secure_port { value 443 } basic__snat { value No } basic__using_ntlm { value No } optimizations__lan_or_wan { value WAN } server_pools__create_new_monitor { value "Create New Monitor" } server_pools__create_new_pool { value "Create New Pool" } server_pools__lb_method_choice { value least-connections-member } server_pools__monitor_http_version { value "Version 1.0" } server_pools__monitor_interval { value 30 } server_pools__monitor_recv { value OK } server_pools__monitor_send { value "GET /" } server_pools__tcp_request_queuing_enable_question { value No } ssl_encryption_questions__cert { value /Common/CopyOfDefault.crt } ssl_encryption_questions__key { value /Common/CopyOfDefault.key } ssl_encryption_questions__offload_ssl { value Yes } }
```

Hopefully this helps. Please let me know of any innacuracies or typos.



***



<br><br><br>
```
╔═╦═════════════════╦═╗
╠═╬═════════════════╬═╣
║ ║ End of Document ║ ║
╠═╬═════════════════╬═╣
╚═╩═════════════════╩═╝
```
<br><br><br>


