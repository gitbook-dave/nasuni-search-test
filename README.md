---
description: >-
  This chapter explains how to install the Nasuni Management Console on your
  network.
---

# Installation

{% hint style="info" %}
**There can be at most one Nasuni Management Console per account.**
{% endhint %}

## Requirements for the Nasuni Management Console

The supported virtual platforms for the NMC include the following:

* Amazon EC2.
* Google Cloud.
* Microsoft Azure.
* Nutanix AHV 5.15.x, AHV 5.16.x, AHV 6.5.x, AHV 6.6.x, AHV 6.7.x, and above.
* VMware ESXi 7.0 and later.
* Microsoft Windows Server Hyper-V version 2016 and later.

### NMC Sizing Guidelines

The NMC requires 32 GB of disk space and 16 GiB of memory (RAM).

Use the following CPU and memory guidelines to plan the sizing of the NMC. These guidelines are based on the number of Edge Appliances managed by the NMC, since the NMC memory and CPU utilization relate directly to the number of Edge Appliances managed.

* If using Varonis, the NMC should have at least 4 CPUs, 16 GiB memory, and an appropriate corresponding virtual machine.

\| Number of Edge Appliancesmanaged by NMC | CPUs | Memory (GiB) | Azure VM size | AWS EC2 instance | | Up to 50 | 2 | 16 | \_ [Standard\_E2s\_v4](https://docs.microsoft.com/en-us/azure/virtual-machines/ev4-esv4-series#esv4-series)\_ | _r5.large_ | | Up to 100 | 4 | 16 | \_ [Standard\_D4s\_v4](https://docs.microsoft.com/en-us/azure/virtual-machines/dv4-dsv4-series#dsv4-series)\_ | _m5.xlarge_ | | Up to 300\* | 8 | 32 | \_ [Standard\_D8s\_v4](https://docs.microsoft.com/en-us/azure/virtual-machines/dv4-dsv4-series#dsv4-series)\_ | _m5.2xlarge_ |

{% hint style="info" %}
If managing more than 200 Edge Appliances, additional backend configuration is necessary for the NMC. Contact Nasuni Support for assistance.
{% endhint %}

**These values are based on CPU and memory utilization for a version 8.5 NMC. Earlier versions of the NMC might require additional resources.**

* These are general recommendations. Your specific situation might require further resources.

## Installing the Nasuni Management Console Software

The Nasuni Management Console runs as a virtual appliance on your network and is distributed as a downloadable image. You need to register on the Nasuni Web site for a user account and password to access the download page.

* When using virtual machine Edge Appliances or NMCs, Nasuni recommends running under a hypervisor that is still supported by its vendor. If a customer runs an Edge Appliance or NMC on anunsupported hypervisor version, a warning is logged at boot time. The warning is of the form:\
  "Nasuni recommends running the Management Console on ESX 7.0 or later."

To download the Nasuni Management Console software from the Nasuni Web site, follow these steps:

1. Using your Web browser, log in to your Nasuni account at \_ [https://account.nasuni.com/account/](https://account.nasuni.com/account/)\_ Click Downloads. The Downloads page appears.

**Download page.**

1. Select the appropriate format for your virtual environment from these choices:
2. AMAZON EC2: Scroll down to the "Appliance AMIs on EC2" area, and follow the instructions to continue installation using appliance AMIs.
3. AZURE FORMAT: A _.vhd_ file, appropriate for Microsoft Azure environments.
4. GOOGLE CLOUD FORMAT: A _disk.raw_ file contained in a _.tar.gz_ file, appropriate for Google Cloud environments.
5. HYPER-V FORMAT:Hyper-V format is appropriate for Microsoft Hyper-V environments: versions 2016 and later.
6. NUTANIX FORMAT: A _.qcow2_ file appropriate forNutanix AHV environments.
7. OVF FORMAT:OVF format is appropriate for VMwareESXi 7.0 and above environments.
8. From the drop-down list, select an available release for the Nasuni Management Console. The list of available releases can change.

**Sample release drop-down list.**

* When performing a recovery procedure, unsupported upgrade paths are blocked. If so, the error message displayed during the procedure might incorrectly state that you are attempting to update to an older version. To avoid this issue, before beginning the recovery process, deploy a Nasuni version that corresponds to the major version of the source appliance.\
  For all supported update paths, see \_ [Compatibility and Support](https://b.link/Nasuni\_Compatibility\_and\_Support\_Information)\_.\
  In summary:
* Edge Appliance update paths:\
  9.12.x → 9.15.x
* NMC update paths:\
  23.2.x → 24.1.x
* If you are running a recovery procedure, select the same version family as your existing Nasuni Management Console to ensure software compatibility. For example, if the existing Nasuni Management Console is running version 21.1, you could select version 21.2 (which is in the same 21.1.x version family), but not version 22.1 (which is in a different version family). If you need to use a different version than those offered, contact Nasuni Customer Support."

**For update paths, see \_** [**Compatibility and Support**](https://b.link/Nasuni\_Compatibility\_and\_Support\_Information)**\_ .**

* You can perform the Recovery process to the same version of the software that you were running, or to a newer version than you were running, but not to an older version.
* If you already have the software installation file, you do not have to download it again. However, the software installation file must not be older than the version you are recovering.
* Save the Nasuni Management Console software _.zip_ file to a location on your local drive.
* Unzip the Nasuni Management Console software .zip file.
* Toinstall the Nasuni Management Console into VMware ESXi, use the vSphere Client to deploy the _NasuniNMC.ovf_ OVF template file. Power on the new Nasuni Management Console virtual machine. Click the _Console_ tab.

Alternatively, to install the Nasuni Management Console into Microsoft Hyper-V, use the Hyper-V Manager to import the virtual machine. Start the new Nasuni Management Console virtual machine. Right-click the Nasuni Management Console virtual machine, and select _Connect_ from the drop-down menu.

Alternatively, to install the Nasuni Management Console into Nutanix AHV, use the Prism Web Console to import the virtual machine. Start the new Nasuni Management Console virtual machine. Right-click the Nasuni Management Console virtual machine, and select _Power On_ from the drop-down menu. Unlike the installation of the Nasuni Edge Appliance, the installation of the Nasuni Management Console requires only one virtual disk.

1. The Nasuni Management Console screen appears with a bar on the bottom that indicates the progress of the installation.

**Nasuni Management Console installation progress screen.**

1. After a few moments, the Nasuni Management Console console screen appears.

**Nasuni Management Console console screen.**

1. If DHCP is available on the network, make note of the IP address that appears on the console screen.

If DHCP is not available, log into the console service screen by pressing Enter and signing in. The default login username is _service_ , and the default password is _service_ . Enter _editnetwork_ . Enter the command: _setall static_ . Enter a new IP address. Note the IP address.

* For security, use the _changepassword_ command to change the password for the service console.
* For more information on console commands, see the \_ [Nasuni Edge Appliance Initial Configuration Guide](https://b.link/Nasuni\_Initial\_Configuration)\_.
* Make note of the initial IP address of your Nasuni Management Console.

## Connecting with the Nasuni Management Console

You should have an initial IP address from the installation of your Nasuni Management Console software on a virtual machine. This IP address might be provided by the IT specialist who initially set up the Nasuni Management Console software.

Open a Web browser and enter the IP address using this command:

**https://**

where is the IP address.

When you attempt to access the Nasuni Management Console Home page for the first time, a message might appear indicating that the security certificate is not trusted. You can still access the Install Wizard to proceed with the initial configuration procedure.

Continue with the next section, [See SSL Security Certificate](Installation.htm#36797).

## SSL Security Certificate

By default, the Nasuni Management Console is preloaded with a self-signed SSL certificate that is unique to the Nasuni Management Console. For this reason, when you attempt to access the Nasuni Management Console Home page for the first time, a message might appear indicating that the security certificate is not trusted. You can still access the Install Wizard to proceed with the initial configuration procedure.

**To add a new SSL certificate, see** [**See SSL Certificates**](ConsoleSettings.htm#92817) **.**

### Example using Mozilla Firefox

This is an example of what you might see using the Mozilla Firefox Web browser:

1. Open a Web browser and enter the IP address provided by the IT specialist who initially set up the Nasuni Management Console. The "This Connection is Untrusted" page appears.

**"This Connection is Untrusted" page.**

1. Click " _I Understand the Risks_". An expanded version of the "This Connection is Untrusted" page appears.

**"This Connection is Untrusted" page.**

1. Click _Add Exception. The Add Security Exception dialog box appears._

**Add Security Exception dialog box.**

1. Click _Get Certificate_.
2. Click _Confirm Security Exception_.
3. Open a Web browser and enter the IP address again.
4. Continue with [See Nasuni Management Console Installation Wizard](Installation.htm#37414).

### Example using Google Chrome

This is an example of what you might see using the Google Chrome Web browser:

1. Open a Web browser and enter the IP address provided by the IT specialist who initially set up the Nasuni Management Console. The "Your connection is not private" page appears.

**"Your connection is not private" page.**

1. Click _Advanced_. The "Your connection is not private" Advanced pane appears.

**"Your connection is not private" Advanced pane.**

1. Click Proceed.
2. Continue with [See Nasuni Management Console Installation Wizard](Installation.htm#37414).

## Nasuni Management Console Installation Wizard

* Edge Appliances and the NMC must be configured with operationalDNS servers and atime server (internal or external) within your environment.

To install the Nasuni Management Console, follow these steps:

1. After you add a security certificate or proceed without adding a security certificate, the Install Wizard — Network Configuration page appears.

**Install Wizard — Network Configuration page.**

1. In the _Hostname or FQDN_ box, a default hostname for the Nasuni Management Console appears. You can accept the default hostname or change it to another hostname. Provide this name to users so that they can access the Nasuni Management Console. You can use ASCII letters a through z, digits 0 through 9, and hyphens.

**The Nasuni Management Console attempts to register the hostname in the DNS server, so that users can access this host by name.**

**To change this name later, see** [**See Networking**](ConsoleSettings.htm#31177) **.**

1. From the _Network Type_ drop-down list, select either _Static_, _DHCP_, orDHCP with Custom DNS.
2. In the Network Device Settings area, enter values depending on your choice of Network Type:
3. DHCP(Dynamic Host Configuration Protocol) orDHCPwith custom DNS: Provides a network IP address for a host on an IP network automatically. The IP Address, Netmask, Default Gateway, and MTU Value fields become unavailable.
4. Static: If you selectStatic as a source, you must provide Network Device Settings. See your IT administrator for assistance.
5. Enter the static IP address in the _IP Address_ text box.
6. Enter anetmask address in the _Netmask_ text box.
7. Enter a default gateway address in the _Default Gateway_ text box.\
   The gateway address must match a subnet of a defined static network.
8. Enter the MTU value in the MTU Value text box. MTU settings above 1500 are supported.\
   The maximum transmission unit (MTU) is the size (in bytes) of the largest protocol data unit that the layer can pass onwards. A larger MTU brings greater efficiency, because each packet carries more user data while protocol overheads, such as headers, remain fixed; the resulting higher efficiency means a slight improvement in the bulk protocol throughput. A larger MTU also means processing fewer packets for the same amount of data. However, large packets can occupy a slow link for some time, causing greater delays to following packets, and increasing lag and minimum latency.
9. In the System Settings area, enter values depending on your choice of Network Type:
10. DHCP(Dynamic Host Configuration Protocol): The Search Domain, Primary DNS Server, and Secondary DNS Server fields become unavailable.
11. Static orDHCPwith custom DNS: If you selectStatic orDHCPwith custom DNS as a source, you must provide System Settings. See your IT administrator for assistance.
12. Enter one or more local search domains in the _Search Domain_ text box. If you enter multiple search domains, make sure you include a space between each entry. You must enter valid hostnames.\
    You can use search domains to avoid typing the complete address of domains that you use frequently. The search domains that you enter are automatically appended to names that you specify for purposes such asActive Directory configuration,HTTPS proxy, andNTP server. For example, if you specify the search domain "mycompany.com", then typing "server1" for one of these purposes would connect to "server1.mycompany.com".

**There are no search domains for LDAP Directory Services.**

* Enter theIP address for yourprimary DNS server in the \_Primary DNS server\_text box. You must enter a valid hostname or IP address.
* Enter the IP address for yoursecondary DNS server in the \_Secondary DNS server\_text box (if applicable). You must enter a valid hostname or IP address.
* Click \_Continue\_to proceed.
* The Install Wizard — Proxy Network Configuration page appears.

**Install Wizard — Proxy Network Configuration page.**

1. To enable proxy support, click _Proxy Support_: On (enabled) or Off (disabled).
2. In the \_Proxy Server\_text box, enter thehostname orIP address of a host running an HTTPS proxy.
3. In the _Port\_text box, enter theport number used by the HTTPS proxy server._\
   _For details about ports and firewalls, see \__ [_Firewall and Port Requirements_](https://b.link/Nasuni\_Firewall\_and\_Port\_Requirements).
4. Optionally, enter a valid username (case-sensitive) for the proxy server in the _User Name_ text box and the password (case-sensitive) in the _Password_ text box.

**The Password cannot include the symbols "/" (slash) and "#" (pound sign).**

1. Optionally, in the _Do Not Proxy_ text box, enter a list of hostnames orIP addresses not to proxy (one per line). Enter one hostname or IP address per line. Do not use a leading period (".").
2. On Azure-based NMCs only, during an installation or recovery procedure, it is necessary to connect with IP address 169.254.169.254 in order to obtain information about the Azure VM instance. If you have configured anHTTPS proxy, this attempt to connect can cause a delay of several minutes. To avoid this delay, add the IP address 169.254.169.254 to the "Do Not Proxy" section of the HTTPS Proxy configuration.
3. Click _Continue_ \_.\_To return to the previous page to change parameters, click Back.
4. The Install Wizard — Review Network Settings page appears.

**Install Wizard — Review Network Settings page.**

To accept the network settings, click _Continue_ . return to the previous page to change parameters, click Back.

1. The Reconfiguring Network Settings page appears.

**Configuring Network Settings page.**

1. If a more recent version of the NMC software is available, a page appears to notify you. Click Continue. A second page appears to notify you of the progress of the software update.
2. The Terms of Service and License Agreement page appears.

**Terms of Service and License Agreement page.**

You can print or download a copy of the Terms of Service and License Agreement by clicking the appropriate button.

Select "I accept the Terms of Service", then click _Continue_ .

1. The Install Wizard —Authorization page appears.

**Install Wizard — Authorization page.**

1. Enter the NMC Serial Number and Authorization code, found at \_ [https://account.nasuni.com/account/serial\_numbers/](https://account.nasuni.com/account/serial\_numbers/)\_.
2. Authorization codes (also called "Auth codes") are intended for a single use, and are not permanent. Authorization codes change if the associatedserial number is used successfully, if the authorization code is refreshed via the NMC (Account Status --> Serial Numbers, then click Refresh), and if the authorization code is regenerated via the NOC (visit \_ [https://account.nasuni.com/account/serial\_numbers/](https://account.nasuni.com/account/serial\_numbers/)\_, then click show, then click regen).
3. Click _Continue_ to proceed.
4. If you reuse an NMC Serial Number for a previously existing Nasuni Management Console, you are asked if you want to perform a disaster recovery procedure on that Nasuni Management Console. For details, see [See Recovery](DisasterRecovery.htm#72784).
5. The Install Wizard — Confirm New NMC Install page appears.

**Install Wizard — Confirm New NMC Install page.**

To add the new Nasuni Management Console, type the words " _Install New NMC_ " (without the quotation marks) in the Confirmation text box, then click Continue.

1. The Install Wizard — Create Admin User page appears.

**Install Wizard — Create Admin User page.**

Create a Username (case-sensitive) and a Password (case-sensitive) for the administrative user of this Nasuni Management Console.

* It is not supported for users in the Active Directory Protected Users security group to log in to the NMC.
* You cannot use Active Directory passwords longer than 127 characters to log in to the NMC.

An indicator of password strength appears. Although password strength is not enforced, you should use strong passwords. This user automatically becomes a member of the NMC Administrators group (see [See Console Users and Groups](ConsoleSettings.htm#64002)). Click Continue.

1. This completes the Install Wizard. The Setup Almost Complete page appears.

**Setup Almost Complete page.**

Follow instructions on this page for placing Nasuni Edge Appliances under the control of the Nasuni Management Console. Click Check for Managed Filers.

Continue with [See Logging in to the Nasuni Management Console](Login.htm#30182).
