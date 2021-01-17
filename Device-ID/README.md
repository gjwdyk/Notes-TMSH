# Device ID



```
╔═════════════════════════════╗
║   Description with Big-IP   ║
╚═════════════════════════════╝
```

ENABLING DEVICE ID+ WITH BIG-IP
1. Log into your BIG-IP (requires version 12.1.0 or later and a provisioned, licensed LTM).
2. Download the Device ID+ iApp template.<br>
   [DeviceID.zip](https://safe-iapp-templates.s3.amazonaws.com/DeviceID.zip) or [DeviceID.zip](DeviceID.zip)
3. Using the template, create an iApp in the BIG-IP as shown here.<br>
   [Getting Started with F5 Device ID+](https://clouddocs.f5.com/cloud-services/latest/f5-cloud-services-DeviceID-GettingStarted.html) or [Getting Started with F5 Device ID+](https://f5cloudservices.zendesk.com/hc/en-us/articles/360060301673-Getting-Started-with-F5-Device-ID-)
4. Copy the link below and paste it into the 1JS URL setting when creating the iApp.<br>
   ```
   https://dip.zeronaught.com/__imp_apg__/js/f5cs-samplesample-xsamplex.js
   ```
5. Save your settings.
6. Paste the page's URL to test your implementation.<br>
   This step requires login to F5's Cloud Services, and paste the inserted web site address into Device ID's Subscription Test field.



```
╔════════════════════════════╗
║   Description with NGINX   ║
╚════════════════════════════╝
```

ENABLING DEVICE ID+ WITH JS SNIPPET<br>
You can inject the JS snippet using a tag management system. Alternatively, you can inject the JS snippet by performing the following steps:
1. Locate the `</head>` tag on the webpages of the sites where you want to collect Device IDs.
2. Copy the code below to insert after the `</head>` tag:<br>
   ```
   <script async defer src="https://dip.zeronaught.com/__imp_apg__/js/f5cs-samplesample-xsamplex.js" id="_imp_apg_dip_" _imp_apg_cid_="f5cs-samplesample-xsamplex" _imp_apg_api_domain_="https://dip.zeronaught.com"></script>
   ```
3. Save the web page.
4. Paste the page's URL to test your implementation.<br>
   This step requires login to F5's Cloud Services, and paste the inserted web site address into Device ID's Subscription Test field.



***



Below are copy-pasted from the iApp template's help, which is hard to read due to layout mistakes.
Note that the iApp is applicable for BOTH Safe (previously Shape Security product) and Device ID.
And the iApp is mostly built for Safe. So selective reading is recommended.

```
╔══════════════════════════════╗
║   The UnReadable iApp Help   ║
╚══════════════════════════════╝
```

### Shape Analytic Products iApp Template

This template creates a complete configuration optimized for the APG application

- [ ] Before you can configure the BIG-IP to work with APG application, ensure that the APG cluster up and running.
- [ ] For a complete walkthrough of this iApp, as well as detailed information and help, see https://github.com/F5Networks/shape-iapp/blob/apg-__TAG__/APG/Deploy%20SAFE%20iApp%20Template%20in%20BIG-IP%2C%20__TAG__.pdf

### General

- [ ] **Product**: Choose the product on which you want to apply the iApp, either SAFE or Device ID+.
- [ ] **Configuration Level**: Choose a configuration level, either Basic or Advanced.
- [ ] **Clean Before Deletion**: Set to Yes to permanently delete the iApp. To complete deletion, click Finished and then delete the iApp from the iApp list at iApps>Application Services>Applications.
- [ ] **Activate Kill-Switch**: Set to Yes to disable, but not permanently delete the iApp. When the iApp is disabled, HTTP requests are sent to the web application’s server directly without any intervention from SAFE or Device ID+.

### JavaScript Injection Configuration

- [ ] **1JS URL**: Enter the full path you received from F5 support for the 1JS injection.
- [ ] **Location for 1JS Injection**: From the drop-down list, select a location in the HTML code of your webpage for the 1JS Injection.
- [ ] **Script Attribute**: Choose an attribute that is added at the end of the injected 1JS, either Async, Sync or Defer. This attribute determines how the JavaScript is loaded and executed.
- [ ] **Inject 1JS in Specific Webpages Only**: Select Yes if you want to inject the 1JS in specific webpages of your web application. Select No to inject the 1JS in all webpages of your web application.
- [ ] **JS Injection Paths**: If you set Inject 1JS in Specific Webpages Only = Yes, enter here the relative paths of the webpages in your application to receive the 1JS injections.
- [ ] **Exclude 1JS Injection from Specific Webpages**: Select Yes if you want to exclude the 1JS from specific webpages in your web application.
- [ ] **JS Excluded Paths**: If you set Exclude 1JS injection from specific webpages = Yes, enter here the relative paths of the webpages in your application where the 1JS injections should be excluded.
- [ ] **Additional 1JS API Endpoints**: If the 1JS is updated with a new endpoint(s) for Telemetry post requests, enter the endpoint(s) provided to you from F5 support here.

### Cookie Decryption and Processing

- [ ] **Note**: This section is relevant only if Product = SAFE.
- [ ] **Endpoints**: Enter here the paths to the web pages on which you want to decrypt and process cookies. Note: Endpoints are not case sensitive (all letters are set to lower case) and must start with ‘/’.
- [ ] **Cookie Name**: Assign a cookie name, or use the assigned default value.
- [ ] **Encryption Key**: Enter the encryption key you received from F5 support for the fraud recommendation cookie. The key has to be base64 encoded.
- [ ] **Header Name to Add**: Assign a header name for the fraud recommendation header, or use the default header name.

### Pool Configuration

- [ ] **Cookie Persistence for Shape Protection Pool**: Select Enable if, after initial load‑balancing, you want HTTP requests of the same session always sent to the same pool member in the Shape Protection Pool. Select Disable if you want the BIG-IP to perform standard load balancing.
- [ ] **Use a Different Domain as a Pool Member**: Set to yes if want all HTTP requests to be directed to a domain that is not the domain in Shape JR URL path.
- [ ] **Domain**: If Use a Different Domain as a Pool Member=Yes, enter here the domain to receive HTTP requests.
- [ ] **Add HTTP Health Check**: Choose whether to perform the HTTP Health Check on the entire pool. The HTTP Health Check is performed in intervals of 5 seconds.

### Virtual Server Configuration

- [ ] **Application’s Virtual Server(s) to Protect**: Select your web application's virtual server(s). Selecting at least one virtual server is mandatory.

### Advanced Features Configuration

- [ ] **Rewrite XFF Header with Connecting IP**: Select Yes to add an XFF header to requests.
- [ ] **Choose a Parent Server-Side SSL Profile for Shape Pool**: If you want to use an SSL profile(s) that is different from what the application pool uses, select it here.
- [ ] **Encrypting Virtual Server IP**: A default IP is assigned. If you have a virtual server already configured to this IP, assign a different IP here.
- [ ] **Use SNI**: Select Yes to use Server Name Indication (SNI) for pool members.
- [ ] **Enable Debug**: Select Yes to enable debug logs.



***



```
╔═════════════════════════════════════════════╗
║   Convert Device ID iApp to TMSH Commands   ║
╚═════════════════════════════════════════════╝
```

Step by step to convert the Device ID iApp into TMSH commands:

- [ ] Deploy the Device ID iApp
- [ ] Refer to [TMSH List All-Properties](https://github.com/gjwdyk/TMSH-Notes/tree/main/Dump-ALL-Configurations), find out all the additional configurations/components which the Device ID iApp made
- [ ] List those additional configurations/components, to see their properties ( reference: [List_Device_ID_Configurations.txt](List_Device_ID_Configurations.txt) )
- [ ] Recreate the additional configurations/components with TMSH command, while adjusting some of the properties value ( reference: [Create_Device_ID_Configurations.txt](Create_Device_ID_Configurations.txt) )
- [ ] For the iRule, refer to [Compose-iRule-from-TMSH](https://github.com/gjwdyk/iRule-Notes/tree/main/Compose-iRule-from-TMSH) to adapt the iRule, so it can be issued from TMSH<br>
      Reference of the original iRule [Original_Device_ID_iRule_from_Device_ID_iApp.txt](Original_Device_ID_iRule_from_Device_ID_iApp.txt)<br>
      Reference of the optimized iRule [Optimized_Device_ID_iRule_from_Device_ID_iApp.txt](Optimized_Device_ID_iRule_from_Device_ID_iApp.txt)



***



```
╔═══════════╗
║   To Do   ║
╚═══════════╝
```

- [ ] Deployment of Device ID with iApp, through the TMSH command



<br><br><br>
```
╔═╦═════════════════╦═╗
╠═╬═════════════════╬═╣
║ ║ End of Document ║ ║
╠═╬═════════════════╬═╣
╚═╩═════════════════╩═╝
```
<br><br><br>


