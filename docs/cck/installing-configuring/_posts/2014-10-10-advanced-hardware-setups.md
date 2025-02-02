---
layout: collection
title: Advanced Hardware Setups
site_section: docs
sub_section: [cck,cck-installing]
pdf: cck/installing-configuring/CCK-Advanced_Hardware_Setups.pdf
pdf-all: true
categories: 
created: 2014-08-13
changed: 2014-08-13
post_author: andygunn
lang: en
---

<img src="{{site.baseurl}}/files/CCK_CommonConfigs_Intro2.png" style="max-width:600px;" />

<section id="introduction">
<h2>Introduction</h2>

<p>For most community wireless networks, installing a few rooftop and window nodes will fit the needs of the neighborhood or town. For others, more complex installations and configurations will be required. This guide follows and is an advanced companion to <a href="{{site.baseurl}}/docs/cck/installing-configuring/common-hardware-setups/">Common Hardware Setups</a>, which covers the most common and basic Commotion configurations.</p>

<p>Sometimes you will need to connect multiple nodes together at a single site, and this guide will help you do that. Some of the instructions below require some familiarity with networking concepts, so we recommend reading through <a href="{{site.baseurl}}/docs/cck/networking/learn-networking-basics/">Learn Networking Basics</a> first.</p>
<p><img src="{{site.baseurl}}/files/CCK_CommonConfigs_buildings.png" style="max-width:590px;" /></p>
</section>


<section id="materials-and-supplies-needed">
<h3>Materials + Supplies needed</h3>

<ol class="rteindent1">
	<li>A printout of the configuration you need, including specific information for the node you are working on.</li>
	<li>Information about the configuration for other nodes in the network.</li>
</ol>

<p><strong>Time required: Varies depending on the complexity - from 20 minutes to an hour.</strong></p>
</section>


<section id="meshing-with-ethernet-dhcp">
<h2>Meshing with Ethernet, with a gateway to the Internet using DHCP for automatic assignment of IP addresses</h2>

<p>If you want to provide a gateway connection to the Internet on your mesh network, it helps to use several nodes at the location hosting that connection. This should reduce bottlenecks that would occur if there were only one node connected to that gateway.</p>
<p><img src="{{site.baseurl}}/files/CCK_CommonConfigs_05_Nodes_meshed_via_Ethernet_with_gateway.png" style="max-width:700px;" /></p>

<p>In the diagram above:</p>
<ul class="rteindent1">
    <li><strong>(A)</strong> Represents a node running the Commotion software.</li>
    <li><strong>(B)</strong> Represents the wireless mesh links between the nodes.</li>
    <li><strong>(C)</strong> Represents the Access Point generated by the Commotion node for users to connect to.</li>
    <li><strong>(D)</strong> Represents an Ethernet switch, which transfers data between all connected devices.</li>
    <li><strong>(E)</strong> Represents Ethernet cabling connecting the modem and nodes to the Ethernet switch.</li>
    <li><strong>(F)</strong> Represents the modem or router from the Internet Service Provider (ISP), connected to the Internet. It provides IP addresses on the local port with DHCP.</li>
    <li><strong>(G)</strong> Represents the Internet.</li>
</ul>
    
<p>The diagram below demonstrates what this would look like with equipment installed on a building:</p>
<p><img src="{{site.baseurl}}/files/CCK_CommonConfigs_05_Nodes_meshed_via_Ethernet_with_gateway_building.png" style="max-width:700px;" /></p>

<p><strong>Steps to Configure:</strong></p>
<p>First, ensure the Commotion nodes mesh with wireless neighbors. Run the Setup Wizard on the first boot, with the same:</p>
<ul class="rteindent1">
    <li><strong>Mesh network name.</strong> By default, this is set to commotionwireless.net.</li>
    <li><strong>Wireless channel.</strong> By default, this is 11 for 2.4GHz wireless devices.</li>
    <li><strong>Mesh encryption password.</strong> The passwords must match across the network. You can also disable encryption across the network.</li>
</ul>

<p>The nodes connected to the modem or router should receive IP addresses and configure themselves as gateways. To ensure the nodes are receiving IP addresses, make sure each node is plugged into the switch, then reboot each node after running Setup Wizard:</p>

<ol class="rteindent1">
    <li>Browse to <strong>Advanced -> System -> Reboot.</strong></li>
    <li>Click “Perform reboot” and wait for the device to restart.</li>
</ol>

<p>Second, set the nodes to “gateway only” to prevent issues with the nodes booting before the modem.</p>

<ol class="rteindent1">
    <li>Browse to the Administration panel on the node.</li>
    <li>Navigate to the <strong>Basic Configuration -> Network Settings -> Additional Network Interfaces</strong> menu.</li>
    <li>In the “Gateway Configuration” pull-down menu, select “This device should ALWAYS try to acquire a DHCP lease”, and make sure “Advertise your gateway to the mesh” is checked.</li>
    <li>"Save and apply" these settings.</li>
</ol>
    
<p>Third, enable meshing over Ethernet for the nodes connected to the switch.</p>

<ol class="rteindent1">
    <li>Browse to the Administration panel on the node.</li>
    <li>Navigate to to the <strong>Advanced -> Services -> OLSR</strong> menu.</li>
    <li>At the bottom of the page, under the interfaces section, click on the "Add" button.</li>
    <li>On the next page, click radio button for the "WAN" interface under "Network".</li>
    <li>In the “Mode” pull down menu, select "Ether".</li>
    <li>Scroll to the bottom of the page and "Save and Apply" these changes.</li>
</ol>

<p>Do these steps for each Commotion node connected to the switch. When all the nodes have been configured, you can confirm that they are meshing over the wired Ethernet connections by connecting to one of the nodes and browsing to the <strong>Basic Menu -> Status</strong>. Then click on “Nearby Mesh Devices” and look under the “OLSR Links” section. You should see entries for all of the nodes connected to the switch, and they should have IP addresses on the same subnet, as given out by the modem or router. These will look like 192.168.x.y, or 10.0.x.y, or something similar. That entry will have an ETX value of 0.100. If this is the case, the nodes are successfully meshing with Ethernet.</p>

<p class="tip">&nbsp;Mounting wireless routers very close to each other can cause interference. For best performance, we recommend:<br/>
1. Mounting equipment on separate poles, with two or three meters (6 to 10 feet) between them.<br/>
2. Using metal shields on the back of directional nodes. These reduce the wireless signal radiated from the back of the equipment, reducing the interference. You can <a href="http://www.rfarmor.com/cart/index.php?main_page=product_info&cPath=12&products_id=30">buy these commercially</a>, or <a href="http://gowasabi.net/content/importance-shielding">make your own from metal building studs</a>.</p>
</section>


<section id="meshing-with-ethernet-no-gateway">
<h2>Meshing with Ethernet, without a gateway to the Internet</h2>

<p>Even if a tall or centrally located site doesn’t have a gateway to the Internet, it may help to mount several wireless nodes there to act as a “supernode” on the network. This can increase throughput on the network and reduce bottlenecks for very busy nodes or nodes with many, many connections on the mesh.</p>
<p><img src="{{site.baseurl}}/files/CCK_CommonConfigs_06_Nodes_meshed_via_Ethernet_with_no_gateway.png" style="max-width:700px;" /></p>

<p>In the diagram above:</p>
<ul class="rteindent1">
    <li><strong>(A)</strong> Represents a node running the Commotion software.</li>
    <li><strong>(B)</strong> Represents the wireless mesh links between the nodes.</li>
    <li><strong>(C)</strong> Represents the Access Point generated by the Commotion node for users to connect to.</li>
    <li><strong>(D)</strong> Represents an Ethernet switch, which transfers data between all connected devices.</li>
    <li><strong>(E)</strong> Represents Ethernet cabling connecting the modem and nodes to the Ethernet switch.</li>
</ul>

<p>The diagram below demonstrates what this would look like with equipment installed on a building:</p>
<p><img src="{{site.baseurl}}/files/CCK_CommonConfigs_06_Nodes_meshed_via_Ethernet_with_no_gateway_building.png" style="max-width:700px;" /></p>

<p><strong>Steps to Configure:</strong></p>
<p>First, ensure the Commotion nodes mesh with wireless neighbors. Run the Setup Wizard on the first boot, with the same:</p>
<ul class="rteindent1">
    <li><strong>Mesh network name.</strong> By default, this is set to commotionwireless.net.</li>
    <li><strong>Wireless channel.</strong> By default, this is 11 for 2.4GHz wireless devices.</li>
    <li><strong>Mesh encryption password.</strong> The passwords must match across the network. You can also disable encryption across the network.</li>
</ul>

<p>The nodes connected to the switch will not receive IP addresses, since there is no modem or router. If the node was previously connected to a router with a DHCP server, disconnect each node and reboot them after running Setup Wizard. This will ensure the nodes do not have incorrect IP address information.</p>
<ol class="rteindent1">
    <li>Browse to <strong>Advanced -> System -> Reboot.</strong></li>
    <li>Click “Perform reboot” and wait for the device to restart.</li>
</ol>

<p>Next, Browse to the Administration panel on the node first node.</p>
<ol class="rteindent1">
    <li>Go to the <strong>Advanced -> Network -> Interfaces</strong> menu</li>
    <ol type="a">
	<li>Under “Interface Overview”, select “Edit” next to the WAN interface.</li>
	<li>Under “Common Configuration”, in the "Protocol" pull down menu, change "Commotion Interface" to "Static Address".</li>
	<li>Click “Switch Protocol” under the prompt “Really switch protocol?”</li>
	<li>Set the static IP on the interface to a private subnet not already in use in the mesh network. For instance, you could set the IP address to 172.16.100.1 and the Netmask to 255.255.255.0. You can leave the gateway and other fields blank.</li>
	<li>Scroll down and “Save and Apply” the settings.</li>
    </ol>
    <li>Add the WAN port to the proper firewall zone.</li>
    <ol type="a">
    	<li><strong>SSH</strong> into the node and type the following commands, hitting the Enter key after each line:</li>
<pre>
uci add_list firewall.@zone[2].network=wan
uci commit firewall
</pre>
	<li>Log off the node with the command “exit”.</li>
    </ol>
    <li>In <strong>Services -> OLSR</strong>, on the General Settings tab, scroll to the bottom and click “Add” in the "Interface" section.</li>
    <ol type="a">
	<li>In the new page that comes up, click the radio button for the "WAN" interface.</li>
	<li>In the “Mode” pull down menu, select "Ether".</li>
	<li>Scroll to the bottom and “save and apply” the settings.</li>
    </ol>
</ol>

<p>Finally, plug each node into the switch and reboot the node one more time. This will ensure the IP address configurations are in the correct state.</p>

<ol class="rteindent1">
    <li>Browse to <strong>Advanced -> System -> Reboot</strong>.</li>
    <li>Click “Perform reboot” and wait for the device to restart.</li>
</ol>

<p>Do these steps for each Commotion node connected to the switch. When you set the IP on those nodes, you must set it to a different address in the same subnet you configured above. In the example given, you would set the addresses to 172.16.100.2, 172.16.100.3, and so on.</p>

<p>Do these steps for each Commotion node connected to the switch. When all the nodes have been configured, you can confirm that they are meshing over the wired Ethernet connections by connecting to one of the nodes and browsing to the <strong>Basic Menu -> Status</strong>. Then click on “Nearby Mesh Devices” and look under the “OLSR Links” section. You should see entries for all of the nodes connected to the switch, and they should have IP addresses on the same subnet, as given out by the modem or router. These will look like 192.168.x.y, or 10.0.x.y, or something similar. That entry will have an ETX value of 0.100. If this is the case, the nodes are successfully meshing with Ethernet.</p>

<p class="tip">&nbsp;Mounting wireless routers very close to each other can cause interference. For best performance, we recommend:<br/>
1. Mounting equipment on separate poles, with two or three meters (6 to 10 feet) between them.<br/>
2. Using metal shields on the back of directional nodes. These reduce the wireless signal radiated from the back of the equipment, reducing the interference. You can <a href="http://www.rfarmor.com/cart/index.php?main_page=product_info&cPath=12&products_id=30">buy these commercially</a>, or <a href="http://gowasabi.net/content/importance-shielding">make your own from metal building studs</a>.</p>
</section>


<section id="meshing-with-ethernet-static-gateway">
<h2>Meshing with Ethernet, with a gateway to the Internet using Static IP addressing</h2>

<p>This example is similar to the other example with a gateway above, but the gateway to the Internet does not provide IP addresses automatically using DHCP. You must configure the addresses for the Commotion nodes manually. In this example the gateway IP address is 192.168.50.1, but you will need to obtain the proper IP address information from your Internet service provider.</p>
<p><img src="{{site.baseurl}}/files/CCK_CommonConfigs_05_Nodes_meshed_via_Ethernet_with_gateway.png" style="max-width:700px;" /></p>

<p>In the diagram above:</p>
<ul class="rteindent1">
    <li><strong>(A)</strong> Represents a node running the Commotion software.</li>
    <li><strong>(B)</strong> Represents the wireless mesh links between the nodes.</li>
    <li><strong>(C)</strong> Represents the Access Point generated by the Commotion node for users to connect to.</li>
    <li><strong>(D)</strong> Represents an Ethernet switch, which transfers data between all connected devices.</li>
    <li><strong>(E)</strong> Represents Ethernet cabling connecting the modem and nodes to the Ethernet switch.</li>
    <li><strong>(F)</strong> Represents the modem or router from the Internet Service Provider (ISP), connected to the Internet. It is configured with a Static IP address, and does not provide IP addresses to clients automatically via DHCP.</li>
    <li><strong>(G)</strong> Represents the Internet.</li>
</ul>
    
<p>The diagram below demonstrates what this would look like with equipment installed on a building:</p>
<p><img src="{{site.baseurl}}/files/CCK_CommonConfigs_05_Nodes_meshed_via_Ethernet_with_gateway_building.png" style="max-width:700px;" /></p>

<p><strong>Steps to Configure:</strong></p>
<p>First, ensure the Commotion nodes mesh with wireless neighbors. Run the Setup Wizard on the first boot, with the same:</p>
<ul class="rteindent1">
    <li><strong>Mesh network name.</strong> By default, this is set to commotionwireless.net.</li>
    <li><strong>Wireless channel.</strong> By default, this is 11 for 2.4GHz wireless devices.</li>
    <li><strong>Mesh encryption password.</strong> The passwords must match across the network. You can also disable encryption across the network.</li>
</ul>

<p>The nodes connected to the switch will not receive IP addresses, since there is no DHCP server. If the node was previously connected to a router with a DHCP server, disconnect each node and reboot them after running Setup Wizard. This will ensure the nodes do not have incorrect IP address information.</p>
<ol class="rteindent1">
    <li>Browse to <strong>Advanced -> System -> Reboot.</strong></li>
    <li>Click “Perform reboot” and wait for the device to restart.</li>
</ol>

<p>Second, you must configure them with static addresses and a static route to the Internet.</p>
<ol class="rteindent1">
    <li>While connected to the node over its WiFi access point, browse to the Administration panel on the first node.</li>
    <li>Go to the <strong>Advanced -> Network -> Interfaces</strong> menu and select “Edit” on the WAN interface.</li>
    <ol type="a">
	<li>Under “Common Configuration”, in the "Protocol" pull down menu, change "Commotion Interface" to "Static Address".</li>
	<li>Click “Switch Protocol”.</li>
	<li>Set the static IP on the interface to the address assigned by the ISP. In our example, the ISP’s modem has the IP address 192.168.50.1. The items to set are:</li>
	<ol type="i">
	    <li>IPv4 IP Address (Given to you by your ISP, one for each node)</li>
	    <li>IPv4 Netmask (normally 255.255.255.0, but may vary)</li>
	</ol>
	<li>Save and apply these settings.</li>
    </ol>
    <li>Add the WAN interface it to the proper firewall zone.</li>
    <ol type="a">
	<li>SSH into the node and type the following commands, hitting the Enter key after each line:</li>
<pre>
uci add_list firewall.@zone[2].network=wan
uci commit firewall
</pre>
	<li>Log off the node with the command “exit”.</li>
    </ol>
    <li>Finally, go to the <strong>Network -> Static Routes</strong> menu.</li>
    <ol type="a">
	<li>Click “Add” in the “Static IPv4 Routes” section.</li>
	<li>In the entry that comes up, select “WAN” in the first pull-down menu.</li>
	<li>In the “Target” field, enter 0.0.0.0</li>
	<li>In the “IPv4-Netmask” field, enter 0.0.0.0</li>
	<li>In the “IPv4-Gateway” field, enter the IP address for the gateway modem or router from the ISP. In our example this is 192.168.50.1</li>
	<li>Save and apply these settings.</li>
    </ol>
    <li>Go to <strong>Services -> OLSR</strong>:</li>
    <ol type="a">
	<li>At the bottom of the page, under the interfaces section, click on the "Add" button.</li>
	<li>On the next page, click radio button for the "WAN" interface under "Network".</li>
	<li>In the “Mode” pull down menu, select "Ether".</li>
	<li>Scroll to the bottom and “Save and apply” the settings.</li>
    </ol>
</ol>

<p>Finally, plug each node into the switch and reboot the node one more time. This will ensure the IP address configurations are in the correct state.</p>
<ol class="rteindent1">
    <li>Browse to <strong>Advanced -> System -> Reboot</strong>.</li>
    <li>Click “Perform reboot” and wait for the device to restart.</li>
</ol>

<p>Do these steps for each Commotion node connected to the switch. When you set the IP on those nodes, you must set it to a different address in the same subnet you configured above. In the example given, you would set the addresses to 192.168.50.3, 192.168.50.4, and so on.</p>

<p>Do these steps for each Commotion node connected to the switch. When all the nodes have been configured, you can confirm that they are meshing over the wired Ethernet connections by connecting to one of the nodes and browsing to the <strong>Basic Menu -> Status</strong>. Then click on “Nearby Mesh Devices” and look under the “OLSR Links” section. You should see entries for all of the nodes connected to the switch, and they should have IP addresses on the same subnet, as given out by the modem or router. These will look like 192.168.x.y, or 10.0.x.y, or something similar. That entry will have an ETX value of 0.100. If this is the case, the nodes are successfully meshing with Ethernet.</p>

<p class="tip">&nbsp;Mounting wireless routers very close to each other can cause interference. For best performance, we recommend:<br/>
1. Mounting equipment on separate poles, with two or three meters (6 to 10 feet) between them.<br/>
2. Using metal shields on the back of directional nodes. These reduce the wireless signal radiated from the back of the equipment, reducing the interference. You can <a href="http://www.rfarmor.com/cart/index.php?main_page=product_info&cPath=12&products_id=30">buy these commercially</a>, or <a href="http://gowasabi.net/content/importance-shielding">make your own from metal building studs</a>.</p>

</section>

<section id="section-definitions">
<h2>Definitions</h2>

<dl>
	<dt>AP (Access Point)</dt>
	<dd>A device that allows wireless devices to connect to a wired network using Wi-Fi or related standards</dd>
	<dt>DHCP: Dynamic Host Configuration Protocol</dt>
	<dd>It assigns IP addresses to client devices, such as desktop computers, laptops, and phones, when they are plugged into Ethernet or connect to Wireless networks.</dd>
	<dt>Ethernet</dt>
	<dd>A type of networking protocol - it defines the types of cables and connections that are used to wire computers, switches, and routers together. Most often Ethernet cabling is Category 5 or 6, made up of twisted pair wiring similar to phone cables.</dd>
	<dt>Router</dt>
	<dd>A device that determines how messages move through a computer network.</dd>
	<dt>Node</dt>
	<dd>An individual device in a mesh network.</dd>
	<dt>WAN: Wide Area Network</dt>
	<dd>Signifies the connection to the global Internet or a different, typically larger, network.</dd>
</dl>

</section>