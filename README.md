# NetworkCommands

NETWORKSETUP(8)           BSD System Manager's Manual          NETWORKSETUP(8)

NAME
     networksetup -- configuration tool for network settings in System Preferences.

SYNOPSIS
     networksetup [-listnetworkserviceorder] [-listallnetworkservices] [-listallhardwareports]
                  [-detectnewhardware] [-getmacaddress hardwareport] [-getcomputername]
                  [-setcomputername computername] [-getinfo networkservice]
                  [-setmanual networkservice ip subnet router] [-setdhcp networkservice [clientid]]
                  [-setbootp networkservice] [-setmanualwithdhcprouter networkservice ip]
                  [-getadditionalroutes networkservice]
                  [-setadditionalroutes networkservice [dest1 mask1 gate1] [dest2 mask2 gate2] ... [destN maskN gateN]]
                  [-setv4off networkservice] [-setv6off networkservice] [-setv6automatic networkservice]
                  [-setv6linklocal networkservice] [-setv6manual networkservice address prefixLength router]
                  [-getv6additionalroutes networkservice]
                  [-setv6additionalroutes networkservice [dest1 prefixlength1 gate1] [dest2 prefixlength2 gate2] ... [des
tN prefixlengthN gateN]]
                  [-getdnsservers networkservice] [-setdnsservers networkservice dns1 [dns2] [...]]
                  [-getsearchdomains networkservice]
                  [-setsearchdomains networkservice domain1 [domain2] [...]]
                  [-create6to4service networkservicename] [-set6to4automatic networkservice]
                  [-set6to4manual networkservice relayAddress] [-getftpproxy networkservice]
                  [-setftpproxy networkservice domain portnumber authenticated username password]
                  [-setftpproxystate networkservice on | off] [-getwebproxy networkservice]
                  [-setwebproxy networkservice domain portnumber authenticated username password]
                  [-setwebproxystate networkservice on | off] [-getsecurewebproxy networkservice]
                  [-setsecurewebproxy networkservice domain portnumber authenticated username password]
                  [-setsecurewebproxystate networkservice on | off] [-getstreamingproxy networkservice]
                  [-setstreamingproxy networkservice domain portnumber authenticated username password]
                  [-setstreamingproxystate networkservice on | off] [-getgopherproxy networkservice]
                  [-setgopherproxy networkservice domain portnumber authenticated username password]
                  [-setgopherproxystate networkservice on | off] [-getsocksfirewallproxy networkservice]
                  [-setsocksfirewallproxy networkservice domain portnumber authenticated username password]
                  [-setsocksfirewallproxystate networkservice on | off]
                  [-getproxybypassdomains networkservice]
                  [-setproxybypassdomains networkservice domain1 [domain2] [...]]
                  [-getproxyautodiscovery networkservice] [-setproxyautodiscovery networkservice on | off]
                  [-getpassiveftp networkservice] [-setpassiveftp networkservice on | off]
                  [-getairportnetwork device] [-setairportnetwork device network [password]]
                  [-getairportpower device] [-setairportpower device on | off]
                  [-listpreferredwirelessnetworks hardwareport]
                  [-addpreferredwirelessnetworkatindex hardwareport network index securitytype [password]]
                  [-removepreferredwirelessnetwork hardwareport network]
                  [-removeallpreferredwirelessnetworks hardwareport]
                  [-getnetworkserviceenabled networkservice]
                  [-setnetworkserviceenabled networkservice on | off]
                  [-createnetworkservice networkservicename hardwareport]
                  [-renamenetworkservice networkservice newnetworkservicename]
                  [-duplicatenetworkservice networkservice newnetworkservicename]
                  [-removenetworkservice networkservice]
                  [-ordernetworkservices service1 [service2] [service3] [...]] [-getMTU hardwareport]
                  [-setMTU hardwarePort value] [-listvalidMTUrange hardwareport] [-getmedia hardwareport]
                  [-setmedia hardwareport subtype [option1] [option2] [...]] [-listvalidmedia hardwareport]
                  [-createVLAN name parentdevice tag] [-deleteVLAN name parentdevice tag] [-listVLANs]
                  [-listdevicesthatsupportVLAN] [-isBondSupported device]
                  [-createBond name [device1] [device2] [...]] [-deleteBond bond]
                  [-addDeviceToBond device bond] [-removeDeviceFromBond device bond] [-listBonds]
                  [-showBondStatus bond] [-listpppoeservices] [-showpppoestatus name]
                  [-createpppoeservice device name account password [pppoeName]]
                  [-deletepppoeservice service] [-setpppoeaccountname service account]
                  [-setpppoepassword service password] [-connectpppoeservice service]
                  [-disconnectpppoeservice service] [-listlocations] [-getcurrentlocation]
                  [-createlocation location [populate]] [-deletelocation location]
                  [-switchtolocation location] [-listalluserprofiles] [-listloginprofiles service]
                  [-enablesystemprofile service on | off] [-enableloginprofile service profile on | off]
                  [-enableuserprofile profile on | off] [-import8021xProfiles service path]
                  [-export8021xProfiles service path yes | no] [-export8021xUserProfiles path yes | no]
                  [-export8021xLoginProfiles service path yes | no]
                  [-export8021xSystemProfile service path yes | no]
                  [-settlsidentityonsystemprofile service path passphrase]
                  [-settlsidentityonuserprofile profile path passphrase] [-deletesystemprofile service]
                  [-deleteloginprofile service profile] [-deleteuserprofile profile] [-version] [-help]
                  [-printcommands]

DESCRIPTION
     The networksetup command is used to configure network settings typically configured in the System Pref-
     erences application.  The networksetup command requires at least "admin" privileges to run. Most of the
     set commands require "root" privileges to run.

     Any flag that takes a password will accept "-" in place of the password to indicate it should read the
     password from stdin.

     A list of flags and their descriptions:

     -listnetworkserviceorder
             Displays a list of network services in the order they are contacted for a connection, along
             with the corresponding port and device for each. An asterisk (*) next to a service means the
             service is inactive.

     -listallnetworkservices
             Displays a list of all the network services on the server's hardware ports. An asterisk (*)
             denotes that a network service is disabled.

     -listallhardwareports
             Displays list of hardware ports with corresponding device name and ethernet address.

     -detectnewhardware
             Detects new network hardware and creates a default network service on the hardware.

     -getmacaddress hardwareport
             Displays ethernet (or Wi-Fi) address for hardwareport or device specified.

     -getcomputername
             Displays the computer name.

     -setcomputername computername
             Sets computer name to <computername>. This name is used by AFP.

     -getinfo networkservice
             Displays the IP address, subnet mask, router, and hardware address for the <networkservice>
             that you specify.

     -setmanual networkservice ip subnet router
             Set the TCP/IP configuration for <networkservice> to manual with IP address set to <ip>, Subnet
             Mask set to <subnet>, and Router address set to <router>.

     -setdhcp networkservice [clientid]
             Use this command to set the TCP/IP configuration for the specified <networkservice> to use
             DHCP. The client ID is optional. Specify "Empty" for [clientid] to clear the DHCP client id.

     -setbootp networkservice
             Use this command to set the TCP/IP configuration for the specified <networkservice> to use
             BOOTP.

     -setmanualwithdhcprouter networkservice ip
             Use this command to specify a manual IP address to use for DHCP for the specified <networkser-
             vice>.

     -getadditionalroutes networkservice
             Use this command to display the list of additional IPv4 routes configured for the service.

     -setadditionalroutes networkservice [dest1 mask1 gate1] [dest2 mask2 gate2] ... [destN maskN gateN]
             Use this command to set the list of IPv4 additional routes configured for the service. Each
             route is specified as a (destination address, subnet mask, gateway address) tuple. Specifying
             no tuples clears the list of routes.

     -setv4off networkservice
             Use this command to turn IPv4 off on the specified <networkservice>.

     -setv6off networkservice
             Use this command to turn IPv6 off on the specified <networkservice>.

     -setv6automatic networkservice
             Use this command to set IPv6 to get its addresses automatically for <networkservice>.

     -setv6linklocal networkservice
             Use this command to set IPv6 to only use link local for <networkservice>.

     -setv6manual ip prefixlength router
             Use this command to set IPv6 to get its addresses manually for <networkservice>. Specify the ip
             address, the prefix length and the router.

     -getv6additionalroutes networkservice
             Use this command to display the list of additional IPv6 routes configured for the service.

     -setv6additionalroutes networkservice [dest1 prefixlength1 gate1] [dest2 prefixlength2 gate2] ...
             [destN prefixlengthN gateN]
             Use this command to set the list of additional routes configured for the service. Each route is
             specified as a
             (destination address, prefix length, gateway address) tuple. Specifying no tuples clears the
             list of routes.

     -getdnsservers networkservice
             Displays DNS info for <networkservice>.

     -setdnsservers networkservice dns1 [dns2] [...]
             Use this command to specify the IP addresses of servers you want the specified <networkservice>
             to use to resolve domain names. You can list any number of servers (replace dns1, dns2, and so
             on with the IP addresses of domain name servers). If you want to clear all DNS entries for the
             specified network service, type "empty" in place of the DNS server names.

     -getsearchdomains networkservice
             Displays Domain Name info for <networkservice>.

     -setsearchdomains networkservice domain1 [domain2] [...]
             Use this command to designate the search domain for the specified <networkservice>. You can
             list any number of search domains (replace domain1, domain2, and so on with the name of a local
             domain). If you want to clear all search domain entries for the specified network service, type
             aemptya in place of the domain name.

     -create6to4service -<newnetworkservicename>
             Use this command to create a new 6 to 4 service with name <newnetworkservicename>.

     -set6to4automatic -<newnetworkservicename>
             Use this command to set the 6 to 4 service such that it will get the relay address automati-

     -set6to4manual -<newnetworkservicename> -<relayaddress>
             Use this command to set the 6 to 4 service such that it will get the relay address manually.
             Specify the <relayaddress> that you would like to set.

     -getftpproxy networkservice
             Displays FTP proxy (server, port, enabled value) info for <networkservice>.

     -setftpproxy networkservice domain portnumber authenticated username password
             Set FTP proxy for <networkservice> with <domain> and <port number>. Turns proxy on. Optionally,
             specify <on> or <off> for <authenticated> to enable and disable authenticated proxy support.
             Specify <username> and <password> if you turn authenticated proxy support on.

     -setftpproxystate networkservice on | off
             Set FTP proxy on <networkservice> to either <on> or <off>.

     -getwebproxy networkservice
             Displays Web proxy (server, port, enabled value) info for <networkservice>.

     -setwebproxy networkservice domain portnumber authenticated username password
             Set Web proxy for <networkservice> with <domain> and <port number>. Turns proxy on. Optionally,
             specify <on> or <off> for <authenticated> to enable and disable authenticated proxy support.
             Specify <username> and <password> if you turn authenticated proxy support on.

     -setwebproxystate networkservice on | off
             Set Web proxy on <networkservice> to either <on> or <off>.

     -getsecurewebproxy networkservice
             Displays Secure Web proxy (server, port, enabled value) info for <networkservice>.

     -setsecurewebproxy networkservice domain portnumber authenticated username password
             Set Secure Web proxy for <networkservice> with <domain> and <port number>. Turns proxy on.
             Optionally, specify <on> or <off> for <authenticated> to enable and disable authenticated proxy
             support. Specify <username> and <password> if you turn authenticated proxy support on.

     -setsecurewebproxystate networkservice on | off
             Set SecureWeb proxy on <networkservice> to either <on> or <off>.

     -getstreamingproxy networkservice
             Displays Streaming proxy (server, port, enabled value) info for <networkservice>.

     -setstreamingproxy networkservice domain portnumber authenticated username password
             Set Streaming proxy for <networkservice> with <networkservice>. Turns proxy on. Optionally,
             specify <on> or <off> for <authenticated> to enable and disable authenticated proxy support.
             Specify <username> and <password> if you turn authenticated proxy support on.

     -setstreamingproxystate networkservice on | off
             Set Streamingproxy on <networkservice> to either <on> or <off>.

     -getgopherproxy networkservice
             Displays Gopher proxy (server, port, enabled value) info for <networkservice>.

     -setgopherproxy networkservice domain portnumber authenticated username password
             Set Gopher proxy for <networkservice> with <domain> and <port number>. Turns proxy on. Option-
             ally, specify <on> or <off> for <authenticated> to enable and disable authenticated proxy sup-
             port. Specify <username> and <password> if you turn authenticated proxy support on.

     -setgopherproxystate networkservice on | off
             Set Gopher proxy on <networkservice> to either <on> or <off>.

     -getsocksfirewallproxy networkservice
             Displays SOCKS Firewall proxy (server, port, enabled value) info for <networkservice>.

     -setsocksfirewallproxy networkservice domain portnumber authenticated username password
             Set SOCKS Firewall proxy for <networkservice> with <domain> and <port number>. Turns proxy on.
             Optionally, specify <on> or <off> for <authenticated> to enable and disable authenticated proxy
             support. Specify <username> and <password> if you turn authenticated proxy support on.

     -setsocksfirewallproxystate networkservice on | off
             Set SOCKS Firewall proxy to  either <on> or <off>.

     -getproxybypassdomains networkservice
             Displays Bypass Domain Names for <networkservice>.

     -setproxybypassdomains networkservice domain1 [domain2] [...]
             Set the Bypass Domain Name Servers for <networkservice> to <domain1> [domain2] [...]. Any num-
             ber of Domain Name servers can be specified. Specify "Empty" for <domain1> to clear all Domain
             Name entries.

     -getproxyautodiscovery networkservice
             Displays Proxy Auto Discover for <networkservice>.

     -setproxyautodiscovery networkservice on | off
             Set Proxy Auto Discover for <networkservice> to either <on> or <off>.

     -getpassiveftp networkservice
             Displays whether Passive FTP is on or off for <networkservice>.

     -setpassiveftp networkservice on | off
             Set Passive FTP to either <on> or <off>.

     -setautoproxyurl networkservice url
             Set proxy auto-config to url for <networkservice> and enable it.

     -getautoproxyurl networkservice
             Displays proxy auto-config (url, enabled) info for <networkservice>.

     -setsocksfirewallproxystate networkservice on | off
             Set SOCKS Firewall proxy to  either <on> or <off>.

     -getairportnetwork hardwareport
             Displays current Wi-Fi Network.

     -setairportnetwork hardwareport network [password]
             Set Wi-Fi Network to <network> using optional [password] if specified.

     -getairportpower hardwareport
             Displays whether Wi-Fi power is on or off.

     -setairportpower hardwareport on | off
             Set Wi-Fi power to either <on> or <off>.

     -listpreferredwirelessnetworks hardwareport
             List the preferred wireless networks for <hardwareport>

     -addpreferredwirelessnetworkatindex hardwareport network index securitytype [password]
             Add wireless network named <network> to preferred list for <hardwareport> at <index>. Store the
             optional password in the keychain For security type, use OPEN for none, WPA for WPA Personal,
             WPA2 for WPA2 Personal, WPA/WPA2 for WPA/WPA2 Personal, WPAE for WPA Enterprise, WPA2E for WPA2
             Enterprise, WPAE/WPA2E for WPA/WPA2 Enterprise, WEP for plain WEP, and 8021XWEP for 802.1X WEP.

     -removepreferredwirelessnetwork hardwareport network
             Remove <network> from the preferred wireless network list for <hardwareport>

     -removeallpreferredwirelessnetworks hardwareport
             Remove all networks from the preferred wireless network list for <hardwareport>

     -getnetworkserviceenabled networkservice
             Displays whether a service is on or off (enabled or disabled).

     -setnetworkserviceenabled networkservice on | off
             Use this command to turn the specified network service on or off (enable or disable).

     -createnetworkservice networkservicename hardwareport
             Create a service named <networkservice> on port <hardwareport>. The new service will be enabled
             by default.

     -renamenetworkservice networkservice newnetworkservicename
             Use this command to rename the specified network service <networkservice> to <newnetworkservi-
             cename>.

     -duplicatenetworkservice networkservice newnetworkservicename
             Use this command to duplicate an existing network service <networkservice> and rename it to the
             specified name <newnetworkservicename>.

     -removenetworkservice networkservice
             Use this command to delete a network service <networkservice>. You cannot use this command to
             delete the last remaining service for a hardware port. To do so, you use the -setnetworkser-
             viceenabled command.

     -ordernetworkservices service1 [service2] [service3] [...]
             Use this command to designate the order network services are contacted on the specified hard-
             ware port. Name the network you want contacted first, then the second, and so on. Use "listnet-
             workserviceorder" to view current service order. Note: use quotes around service names which
             contain spaces (ie. "Built-in Ethernet").

     -setMTUAndMediaAutomatically hardwarePort
             Set hardwareport or device specified back to automatically setting the MTU and Media.

     -getMTU hardwareport
             Get the MTU value for hardwareport or device specified.

     -setMTU hardwarePort value
             Set MTU for hardwareport or device specified.

     -listValidMTURange hardwareport
             List the valid MTU range for hardwareport or device specified.

     -getMedia hardwareport
             Show both the current setting for media and the active media on hardwareport or device speci-
             fied.

     -setMedia hardwareport subtype [option1] [option2] [...]
             Set media for hardwareport or device specified to subtype. Specify optional [option1] and addi-
             tional options depending on subtype. Any number of valid options can be specified.

     -listValidMedia hardwareport
             List valid media options for hardwareport or device name. Enumerates available subtypes and
             options per subtype.

     -createVLAN name parentdevice tag
             Create a VLAN with the name <name> over the parent device <parentdevice> and with the tag
             <tag>.

     -deleteVLAN name parentdevice tag
             Delete the VLAN with the name <name> over the parent device <parentdevice> and with the tag
             <tag>.

     -listVLANs
             List the VLANs that have been created.

     -listdevicesthatsupportVLAN
             List the devices that support VLANs.

     -isBondSupported device
             Displays YES if the device can be added to a bond. NO if it cannot.

     -createBond name [device1] [device2] [...]
             Create a bond with the user-defined-name name and optionally add any listed devices if they
             support bonding.

     -deleteBond bond
             Delete the bond with the specified device-name.

     -addDeviceToBond device bond
             Add device to bond.

     -removeDeviceFromBond device bond
             Remove device from bond.

     -listBonds
             List of all bonds.

     -showBondStatus bond
             Display the status of the specified bond.

     -listpppoeservices
             List all PPPoE services in the current set.

     -showpppoestatus name
             Display the status of the PPPoE service with the specified name.

     -createpppoeservice device name account password [pppoeName]
             Create a PPPoE service on the specified device with the service name specified.

     -deletepppoeservice service
             Delete the service.

     -setpppoeaccountname service account
             Set the account name for the service.

     -setpppoepassword service password
             Set the password for the service.

     -connectpppoeservice service
             Connect the service.

     -disconnectpppoeservice service
             Disconnect the service.

     -listlocations
             List all network locations.

     -getcurrentlocation
             Display the name of the current set.

     -createlocation location [populate]
             Create a set with the user-defined-name name and optionally populate it with the default ser-
             vices.

     -deletelocation location
             Delete the set.

     -switchtolocation location
             Make the specified set the current set.

     -listalluserprofiles
             Display the names of all of the user profiles.

     -listloginprofiles service
             Display the names of the loginwindow profiles for the specified service.

     -enablesystemprofile service on | off
             Enables or disables the system profile for the specified service.

     -enableloginprofile service profile on | off
             Enables or disables the specified loginwindow profile for the specified service.

     -enableuserprofile profile on | off
             Enables or disables the specified user profile.

     -import8021xProfiles service path
             Imports the 802.1x profiles for the specified service.

     -export8021xProfiles service path yes | no
             Exports all of the profiles for the specified service and optionally includes the items from
             the keychain.
     -export8021xUserProfiles path yes | no
             Exports only the user profiles and optionally includes the items from the keychain.

     -export8021xLoginProfiles service path yes | no
             Exports only the loginwindow profiles for the specified service  and optionally includes the
             items from the keychain.

     -export8021xSystemProfile service path yes | no
             Exports only the system profile for the specified service and optionally includes the items
             from the keychain.

     -settlsidentityonsystemprofile service path passphrase
             Sets the TLS identity on the system profile for the specified service. Identity must be a
             pkcs12 file.

     -settlsidentityonuserprofile profile path passphrase
             Sets the TLS identity on the specified user profile. Identity must be a pkcs12 file.

     -deletesystemprofile service
             Deletes the system profile for the specified service.

     -deleteloginprofile service profile
             Deletes the specified loginwindow profile for the specified service.

     -deleteuserprofile profile
             Deletes the specified user profile.  Displays version of networksetup tool.

     -help   Displays a list of all the commands available in the Network Setup Tool, with explanatory
             information.

     -printcommands
             Displays a list of commands with no detail.

EXAMPLES
     networksetup -listallnetworkservices

     networksetup -setmanual "Built-in Ethernet" 192.168.100.100 255.255.255.0 192.168.100.1

     networksetup -setdnsservers "Built-in Ethernet" 192.168.100.100 192.168.100.12

     networksetup -setsearchdomains "Built-in Ethernet" company.com corp.com

     networksetup -setwebproxy "Built-in Ethernet" proxy.company.com 80

     networksetup -setwebproxy "Built-In Ethernet" proxy.company.com 80 On authusername authpassword

     networksetup -duplicatenetworkservice "Built-In Ethernet" "Local LAN"

     networksetup -getdnsservers "Built-In Ethernet"

     networksetup -setMTU en0 1500

     networksetup -setMedia en0 autoselect

     networksetup -setMedia en0 100baseTX half-duplex

     networksetup -createBond MyBond en0 en1

     networksetup -addDeviceToBond en0 bond0

     networksetup -setpppoepassword MyPPPoE - < ~/Desktop/MyPasswordFile.txt

     networksetup -createlocation Home populate

     networksetup -import8021xProfiles Ethernet "/Users/MyHome/Downloads/ExportedConfigs.networkconnect"

FILES
     /usr/sbin/networksetup

SEE ALSO
     systemsetup(8)

Mac OS X                        April 16, 2002                        Mac OS X
(END)
