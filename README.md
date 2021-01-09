# TMSH-Notes


***



<a href="https://github.com/gjwdyk/CloudFormation-Big-IP-LAMPv7">![Network Diagram](https://raw.githubusercontent.com/gjwdyk/CloudFormation-Big-IP-LAMPv7/master/Figures/LogicalNetworkDiagramWindows.png)</a>

Referring to the [CF_BigIP_LAMP_Win_SSLoL_eMail_Lidsa_AS3.20_AddOn.json](CF_BigIP_LAMP_Win_SSLoL_eMail_Lidsa_AS3.20_AddOn.json) template creates:
1. One F5's LAMPv7 instance which had been adapted to AWS environment in certain extend.
2. One F5's Windows Server 2008 R2 instance which had been adapted to AWS environment in certain extend.
3. One F5's Big-IP instance, license the instance, configure the networking part, and potentially also configure the services with the AS3 Declaration URL.
4. Import the TLS Private Key and Certificate into the Big-IP, so the corresponding AS3 Declaration can use them to create SSL Profiles.
5. Configure SSMTP and user_alert.conf to send email notification in case of an event. The example works with GMail's SMTP, and sending notification when a pool has no available member, and when the pool back to having a member available to handle the traffic.
6. Lorem Ipsum Dolor Sit Amet mock-up field.
7. Upgrade F5 Application Services 3 Extension from previous version 3.5.1-5 into version 3.20.0-3 .
8. Improved OnBoarding to support Add-On Module Registration/Licensing.

Default AS3 Declaration for [CF_BigIP_LAMP_Win_SSLoL_eMail_Lidsa_AS3.20_AddOn.json](CF_BigIP_LAMP_Win_SSLoL_eMail_Lidsa_AS3.20_AddOn.json) is [AS3-LTM-SSLoL-AVR-NOutB](AS3-LTM-SSLoL-AVR-NOutB/), but can be changed during the CloudFormation template deployment,
provided the replacement AS3 Declaration fits into the Big-IP environment provided by the [CF_BigIP_LAMP_Win_SSLoL_eMail_Lidsa_AS3.20_AddOn.json](CF_BigIP_LAMP_Win_SSLoL_eMail_Lidsa_AS3.20_AddOn.json) template.


<a href="https://console.aws.amazon.com/cloudformation/home?region=ap-southeast-1#/stacks/new?stackName=BigIP-LAMP-Win&templateURL=https://aws-f5-singapore-hc-demo-bucket-files.s3-ap-southeast-1.amazonaws.com/CF/CF_BigIP_LAMP_Win_SSLoL_eMail_Lidsa_AS3.20_AddOn_Original.json"><img align="right" src="https://github.com/gjwdyk/CloudFormation-Big-IP-LAMPv7/raw/master/Figures/LaunchStackJigokuShoujo.png" width="140" height="22"/></a>
<a href="https://console.aws.amazon.com/cloudformation/home?region=ap-southeast-1#/stacks/new?stackName=BigIP-LAMP-Win&templateURL=https://aws-f5-singapore-hc-demo-bucket-files.s3-ap-southeast-1.amazonaws.com/CF/CF_BigIP_LAMP_Win_SSLoL_eMail_Lidsa_AS3.20_AddOn.json"><img src="https://github.com/gjwdyk/CloudFormation-Big-IP-LAMPv7/raw/master/Figures/JigokuShoujoLaunchStack.png" width="140" height="22"/></a>



***


To Do:

- [ ] Update existing AS3 with Pools from Windows Server ??? (should we do this or not?)
- [ ] Update Previous CF templates to use No OutBound versions of AS3 (and Update the corresponding Documentations)
- [ ] tmsh modify sys db ui.statistics.modulestatistics.localtraffic.persistencerecords value true
- [ ] Test Concept of Floating IP for High Availability. If 2 interfaces assigned same IP Address, will they be conflict? If not assigned, will they work?
- [ ] Default ASM Profiles
- [ ] APM (when applicable)



***


