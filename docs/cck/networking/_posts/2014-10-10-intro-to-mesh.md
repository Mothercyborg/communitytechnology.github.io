---
layout: collection
title: Introduction to Mesh
description: An introduction to mesh and network properties.
pdf: cck/networking/2-Introduction_to_Mesh.pdf
pdf-all: true
created: 2013-11-11
changed: 2013-12-02
lang: en
---

<section id="introduction">
<h2>Introduction</h2>

<p>There are many ways to build networks and many technologies you can use. This module is an introduction to the idea of how mesh networks work and how they are different from other kinds of networks. Understanding mesh networking is important for designing your network, and for talking to people in your neighborhood who may want to support or be involved with your project.</p>

<p>Read and discuss the ideas below, then use <a href="{{site.baseurl}}/files/cck/networking/2.1-Name_That_Network.pdf">Name that Network</a> to explore the different properties of networks. The questions and activities in the slides will help everyone think about different network structures.</p>

<p>By exploring different networks structures, you will get a sense for how to think about network design and how different designs are useful in different situations.</p>

<p><strong>Time required: 30 minutes to review and discuss the text. 45 minutes for the presentation and activities. </strong></p>
</section>

<section id="materials-and-supplies-needed">
<h3>Materials</h3>

<p><a href="{{site.baseurl}}/files/cck/networking/2.1-Name_That_Network.pdf"><img src="{{site.baseurl}}/files/cck/intro_to_mesh_presentation.png?itok=GLXiZJfZ" style="width:50%"/></a></p>

<p>Printouts of <strong><a href="{{site.baseurl}}/files/cck/networking/2.1-Name_That_Network.pdf">Name that Network</a>&nbsp;</strong>(optional)</p>
</section>

<section id="read-and-discuss">
<h2>Read and Discuss</h2>

<p>Read and discuss the information below. To further explore the characteristics of different types of networks, go through <a href="{{site.baseurl}}/files/cck/networking/2.1-Name_That_Network.pdf"><strong>Name that Network</strong></a>.</p>

<h4>1. Networks can have a hierarchical or mesh structure.</h4>

<div class="display:table; width:100%; text-align:center;">

  <div style="float:left; width: 30%; margin: 0 10%; align:center;">
    <p><img src="{{site.baseurl}}/files/cck/learn_about_mesh_hier_dots.png" /></p><p>Hierarchical / Hub and Spoke</p>
  </div>
  <div style="float:left; width: 30%; text-align:center;">
    <p><img src="{{site.baseurl}}/files/cck/learn_about_mesh_mesh_dots.png?itok=hlYSgvH6"  /></p><p>Mesh</p>
  </div>

</div>

<div style="width:100%; display:table;">
  <p>Networks are groups of connected devices that move information or messages from one place to another.</p>
  
  <p>Most networks (including cellular phone networks) use a “hub and spoke” or hierarchical architecture, with users connecting to other users via a central device that controls connections and traffic on the network.</p>
  
  <p>This means that any time you communicate through the network, the message or data must first go to that central hub, then be sent on to its destination.</p>
</div>

<h4>2. Mesh networks route differently than non-mesh networks.</h4>
<div style="align:center; display:table; width:100%;">
<p><img src="{{site.baseurl}}/files/cck/learn_about_mesh_hier_route.png?itok=cqjyQu5M" style="width:30%; float:left; margin:0 10%;"/><img src="{{site.baseurl}}/files/cck/learn_about_mesh_mesh_route.png" style="width:30%; float:left;"/></p>
</div>
<div>
<p>The difference between mesh networks and other kinds of networks is that mesh networks use a particular kind of protocol for moving information from one place to another.</p>
</div>

<h4>3. Routers are devices that determine how information moves across the network.</h4>

<div>
  <p><img src="{{site.baseurl}}/files/cck/learn_about_mesh_router_laptops.png?itok=OLtgrlQl" style="width: 200px; height: 126px;" typeof="foaf:Image" /></p>
</div>
<div>
<p>Standard access points, like the one you might have at home, talk to computers or smartphones, but they cannot easily talk to other routers.</p>
</div>

<h4>4. Mesh-enabled routers can dynamically talk to each other, allowing them to flexibly route traffic within the network.</h4>

<table border="0" cellpadding="0" cellspacing="0" style="width: 100%;">
  <div>
    <p><img src="{{site.baseurl}}/files/cck/learn_about_mesh_simple_routers.png?itok=BATFARzr" style="width: 50%" typeof="foaf:Image" /></p>
  </div>
  <p>By default, most routers and devices are not able to mesh. But, with the right operating system, some routers, cellphones and laptops can mesh.</p>
  
  <p>You build a mesh network by installing an open-source mesh software package on wireless-enabled devices, and then connecting them to other nearby meshing devices.</p>
</div>

<h4>5. Any mesh device can be the hub or central point in the network – or the network can have no central point.</h4>

<div>
  <p><img src="{{site.baseurl}}/files/cck/learn_about_mesh_complex_routers.png?itok=__3JG6ZT" style="width: 70%" typeof="foaf:Image" /></p>
</div>
<div>
  <p>The more devices that are part of the mesh network, the more flexible the network becomes. Any mesh device can be the hub or central point in the network – or the network can have no central point.</p>
</div>

<h4>6. Any mesh device can form the edge of the network, able to extend its reach and form new connections.</h4>

<div>
  <p><img src="{{site.baseurl}}/files/cck/learn_about_mesh_complex_routers2.png?itok=hkniUJ93" style="width: 70%" typeof="foaf:Image" /></p>
</div>
<div>
  <p>A dynamic mesh network, unlike a more “static” traditional network, constantly adapts to new conditions. It automatically adjusts its pathways to integrate new nodes that join the network and has the flexibility to reroute information when a node leaves the network.</p>
</div>

<h4>7. Mesh networks are strengthened and expanded as the user base grows.</h4>

<div>
  <p><img src="{{site.baseurl}}/files/cck/learn_about_mesh_complex_routers3.png?itok=U9gFTEEu" style="width: 70%;" typeof="foaf:Image" /></p>
</div>
<div>
  <p>When there are many interconnected mesh nodes, the network can bypass interference, blockage, or network congestion.</p>
  
  <p>When your friend sends a reply text to you, if one of the nodes stops working, the mesh network will adapt accordingly, ensuring you get the message.</p>

</div>
</section>
<section>
<p>To further explore the characteristics of different types of networks, go through&nbsp;<strong><a href="{{site.baseurl}}/files/cck/networking/2.1-Name_That_Network.pdf">Name that Network</a></strong>.</p>

<p>Once you have an understanding about the basics of mesh, try putting your knowledge into practice with the <strong><a href="{{site.baseurl}}/docs/cck/planning/design-your-network-every-network-tells-story">Every Network Tells a Story</a></strong> module. For more technical information on how Commotion works and forms a mesh network, <strong>Learn about Wireless&nbsp;(coming soon).</strong></p>

</section>

<section id="section-definitions">
<h2>Definitions</h2>

<dl>
	<dt>Hierarchical</dt>
	<dd>In this case, hierarchical refers to the tree-structured client and master relationship between devices in traditional networks.</dd>
	<dt>Hops</dt>
	<dd>The number of links required to reach a destination node on the network.</dd>
	<dt>Many-to-many</dt>
	<dd>In mesh networks, many nodes can connect to many nodes. &nbsp;In traditional designs, one node may connect to one or one node can connect to many.</dd>
	<dt>Mesh</dt>
	<dd>A type of network in which nodes can connect as peers and dynamically route traffic across the network.</dd>
	<dt>Router</dt>
	<dd>A device that determines how messages move through a computer network.</dd>
</dl>
</section>

<section class="related-information" id="section-related-information">
<h2>Related Information</h2>

<p>To explore these concepts further, look at<strong>&nbsp;Learn about Wireless&nbsp;(coming soon).</strong></p>

<p>Once you have an understanding about the basics of mesh, try putting your knowledge into practice with the <a href="{{site.baseurl}}/docs/cck/planning/design-your-network-every-network-tells-story"><strong>Every Network Tells a Story</strong></a> module.</p>
</section>
 
