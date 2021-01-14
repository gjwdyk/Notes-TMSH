# Device ID



```
╔═════════════════════════════╗
║   Description with Big-IP   ║
╚═════════════════════════════╝
```

ENABLING DEVICE ID+ WITH BIG-IP
1. Log into your BIG-IP (requires version 12.1.0 or later and a provisioned, licensed LTM).
2. Download the Device ID+ iApp template.<br>
   https://safe-iapp-templates.s3.amazonaws.com/DeviceID.zip
3. Using the template, create an iApp in the BIG-IP as shown here.<br>
   https://clouddocs.f5.com/cloud-services/latest/f5-cloud-services-DeviceID-GettingStarted.html<br>
   https://f5cloudservices.zendesk.com/hc/en-us/articles/360060301673-Getting-Started-with-F5-Device-ID-<br>
   https://github.com/F5Networks/shape-iapp/blob/apg-__TAG__/APG/Deploy%20SAFE%20iApp%20Template%20in%20BIG-IP%2C%20__TAG__.pdf<br>
4. Copy the link below and paste it into the 1JS URL setting when creating the iApp.<br>
   ```
   https://dip.zeronaught.com/__imp_apg__/js/f5cs-a_aaN4ZQjkl0-3cfe4298.js
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
1. Locate the </head> tag on the webpages of the sites where you want to collect Device IDs.
2. Copy the code below to insert after the </head> tag:<br>
   ```
   <script async defer src="https://dip.zeronaught.com/__imp_apg__/js/f5cs-a_aaN4ZQjkl0-3cfe4298.js" id="_imp_apg_dip_" _imp_apg_cid_="f5cs-a_aaN4ZQjkl0-3cfe4298" _imp_apg_api_domain_="https://dip.zeronaught.com"></script>
   ```
3. Save the web page.
4. Paste the page's URL to test your implementation.<br>
   This step requires login to F5's Cloud Services, and paste the inserted web site address into Device ID's Subscription Test field.



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


