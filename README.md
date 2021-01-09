# TMSH-Notes



***



This repository refers to the [CloudFormation-Big-IP-LAMPv7](https://github.com/gjwdyk/CloudFormation-Big-IP-LAMPv7) repository with the diagram as below:
![Network Diagram](https://raw.githubusercontent.com/gjwdyk/CloudFormation-Big-IP-LAMPv7/master/Figures/LogicalNetworkDiagramWindows.png)

The AS3 (F5 Application Services 3 Extension) builds configurations within specific partition (other than the default `/Common/` partition).
However F5 new features such as Device ID+ is currently NOT compatible with partition configurations.
Furthermore AS3's capabilities in configuring F5 unit is still limited to fairly basic components only.

To use the scripts, launch the [CF_BigIP_LAMP_Win_SSLoL_eMail_Lidsa_AS3.20_AddOn.json](CF_BigIP_LAMP_Win_SSLoL_eMail_Lidsa_AS3.20_AddOn.json) CloudFormation template:

<a href="https://console.aws.amazon.com/cloudformation/home?region=ap-southeast-1#/stacks/new?stackName=BigIP-LAMP-Win&templateURL=https://aws-f5-singapore-hc-demo-bucket-files.s3-ap-southeast-1.amazonaws.com/CF/CF_BigIP_LAMP_Win_SSLoL_eMail_Lidsa_AS3.20_AddOn_Original.json"><img align="center" src="https://github.com/gjwdyk/CloudFormation-Big-IP-LAMPv7/raw/master/Figures/JigokuShoujoLaunchStack.png" width="140" height="22"/></a>

AND input `none` into parameter "AS3 Declaration URL".

License needed of type : F5-BIG-VE-LAB-V18-LIC (or equivalent).

Module(s) to be provisioned : LTM, AVR, ASM, FPS, AFM ( `ltm:nominal,avr:nominal,asm:nominal,fps:nominal,afm:nominal` ). Provisionable modules are: afm, am, apm, asm, avr, cgnat, dos, fps, gtm, ilx, lc, ltm, pem, sslo, swg, urldb .

After the CloudFormation finished AND the Big-IP on-boarding process (Configure Network, License and Provision) finished; login to Big-IP SSH CLI and execute the scripts in [F5_Configurations.txt](F5_Configurations.txt) line by line.



***



To Do:

- [ ] Device ID Configuration
- [ ] DDoS Configuration
- [ ] ASM Configuration (when possible)
- [ ] APM Configuration (when possible)
- [ ] Translate to Ansible



***


