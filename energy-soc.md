---
layout: page
title: Energy Harvesting SoC
description: A full tapeout on TSMC 28nm of a custom SoC design with a custom ADC in a team of 3.
image: assets/images/chip.png
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
<p><span class="image right"><img src="{% link assets/images/chip.png %}" alt="" /></span>As part of the 18-725 Advanced Digital Integrated Circuit Design class and with a group of 2 other students, we successfully brainstormed, designed, ran through the flow, and taped out a mixed signal chip on TSMC 28nm. The chip features a custom RISC-V core with the ability to halt and transparently resume execution in the case of low power, a custom synthesizable 10 bit ADC designed, laid out, and pushed through flow by myself as a Digital-on-Top setup, and logic to store ADC values to offboard FRAM during low power states while the core is disabled.</p>

<hr class="major" />

<h2 id="features">Features</h2>
<ul>
    <li>TSMC 28nm Process</li>
    <li>Full tapeout on team of 3, with custom design</li>
    <li>32bit RISC-V core w/ F and M extensions</li>
    <ul>
        <li>1KiB instruction cache</li>
        <li>1KiB data cache</li>
        <li>100MHz core clock</li>
        <li>Power loss resilient: non-volatile RAM, stores CPU state (PC, registers, etc)</li>
        <li>Clock gated for shutoff in low power scenarios</li>
        <li>SPI I/O</li>
    </ul>
    <li>Custom synthesizable 10-bit ADC</li>
    <ul>
        <li>1kHz sampling rate</li>
        <li>2069um^2 area</li>
        <li>7uW avg power usage</li>
        <li>3.32bit INL, 4.25bit DNL</li>
    </ul>
    <li>6.591mW core on power usage, 3.67mW core off power usage</li>
</ul>

<h2 id="operation">Operation</h2>
<span class="image fit"><img src="{% link assets/images/block_diagram.png %}" alt="" /></span>

The chip is designed to be used in areas of low-energy availability, where the only energy source is harvested energy such as from
solar panels, that gets stored in a supercapacitor or battery. The advantage of this setup is that these devices, which are frequently
used to log data and inform decisions, don't need complicated infrastructure to be setup, and can run for years.

The challenges with this setup is the reliability of energy, requiring that any chips use low power and are ready to shutoff to
conserve power. Our chip has a programmable RISC-V CPU core that allows arbitrary workloads and edge computing to be done, but this
core is only enabled when a signal to the core indicates that there is enough energy available. If there is not, then the entire state
of the CPU is saved so that on next power on, the CPU can resume transparently and without needing to know that it was ever shutoff.

When the core is turned off, our ADCs connect directly to offchip non-volatile memory so that data can still be collected and transmitted
once enough energy is available, ensuring that there is no data loss.

Our custom synthesizable ADCs have the advantage of using very little energy, as low as 7uW, with acceptable accuracy. Given the applications
of sensing the environment, the low sampling rate is an acceptable tradeoff for this performance. This mixed signal ADC was modeled in Verilog-AMS,
laid out with some hand layout together with synthesized digital logic for controlling the SAR ADC, and all validated with spectre.
