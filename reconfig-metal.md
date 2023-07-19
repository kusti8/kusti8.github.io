---
layout: page
title: Reconfigurable Metal Array
description: A reconfigurable array of MOSFETS, resistors, and capacitors hand laid out on Skywater 130nm
image: assets/images/reconfig_layout.png
nav-menu: true
---

<!-- Main -->
<div id="main" class="alt">

<!-- One -->
<section id="one">
	<div class="inner">
		<header class="major">
			<h1>Energy Harvesting SoC</h1>
		</header>

<!-- Content -->
<h2 id="content">Overview</h2>
<p><span class="image right"><img src="{% link assets/images/reconfig_layout.png %}" alt="" /></span>
As part of a research group working on a lab on a chip system, I implemented a reconfigurable metal array using MOSFETS,
poly resistors, and MiM capacitors to allow small arbitrary analog and digital systems to be laid out post tapeout. This is
done using laser etching with gold on the highest metal layer. It features small arrays that can be laid out
as space permits and has been designed to allow easy routing, given the restrictive sizes of traces required. For the etching,
the metal runs have to be at least 2um wide and have 2um of space between eachother. It has been taped out in Skywater 130nm. Below is a sample
circuit using the array.</p>

<span class="image fit"><img src="{% link assets/images/reconfig_opamp.png %}" alt="" /></span>
