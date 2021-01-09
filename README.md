# TMSH-Notes


***


This repository refers to the [CloudFormation-Big-IP-LAMPv7](https://github.com/gjwdyk/CloudFormation-Big-IP-LAMPv7) repository with the diagram as below:
<a href="https://github.com/gjwdyk/CloudFormation-Big-IP-LAMPv7">![Network Diagram](https://raw.githubusercontent.com/gjwdyk/CloudFormation-Big-IP-LAMPv7/master/Figures/LogicalNetworkDiagramWindows.png)</a>

The AS3 (F5 Application Services 3 Extension) builds configurations within specific partition (other than the default /Common/ partition).
However F5 new features such as Device ID+ is currently NOT compatible with partition configurations.
Furthermore AS3's capabilities in configuring F5 unit is still limited to fairly basic components only.

To use the scripts, launch the [CF_BigIP_LAMP_Win_SSLoL_eMail_Lidsa_AS3.20_AddOn.json](CF_BigIP_LAMP_Win_SSLoL_eMail_Lidsa_AS3.20_AddOn.json) CloudFormation template:
<a href="https://console.aws.amazon.com/cloudformation/home?region=ap-southeast-1#/stacks/new?stackName=BigIP-LAMP-Win&templateURL=https://aws-f5-singapore-hc-demo-bucket-files.s3-ap-southeast-1.amazonaws.com/CF/CF_BigIP_LAMP_Win_SSLoL_eMail_Lidsa_AS3.20_AddOn_Original.json"><img align="center" src="https://github.com/gjwdyk/CloudFormation-Big-IP-LAMPv7/raw/master/Figures/JigokuShoujoLaunchStack.png" width="140" height="22"/></a>
AND input "none" (without the quotes) into parameter "AS3 Declaration URL".

License needed of type : F5-BIG-VE-LAB-V18-LIC (or equivalent)
Module to be provisioned : LTM, AVR, ASM, FPS, AFM (ltm:nominal,avr:nominal,asm:nominal,fps:nominal,afm:nominal). Provisionable modules are: afm, am, apm, asm, avr, cgnat, dos, fps, gtm, ilx, lc, ltm, pem, sslo, swg, urldb .

After the CloudFormation finished AND the Big-IP on-boarding process (Configure Network, License and Provision) finished; login to Big-IP SSH CLI and execute the scripts.




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


