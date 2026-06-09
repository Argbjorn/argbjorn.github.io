---
layout: page
title: Chrome extensions pack
description: Simple extensions for internal puprposes
img: assets/img/p2_preview.jpg
importance: 2
category: work
related_publications: false
---

I work at Petrovich-Tech, where we develop a large e-commerce platform. During frontend testing, our team frequently runs into repetitive manual tasks. I enjoy automating routine work, so I built a few Google Chrome extensions to make part of our job easier. There's nothing technically groundbreaking about these extensions, but they're a good example of how a small effort can save a decent amount of time.

<h2>Petrovich Cookie Manager</h2>
We have several test cookies and URL parameters that we toggle during site testing. Creating or editing a cookie manually through DevTools takes multiple clicks and keyboard input. My extension edits the relevant cookies directly, with preset values ready to apply. It works across all our test environments and includes a visual indicator when a test cookie is active.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/p2_1.jpg" title="Petrovich Cookie Manager" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<h2>Petrovich Quick GUID Viewer</h2>
A minimalist extension for viewing and easily copying a product's GUID. Our internal systems rely heavily on GUIDs, but they're buried inside network requests.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/p2_2.jpg" title="Petrovich Quick GUID Viewer" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<h2>What's on prod</h2>
My first and smallest extension. We often want to compare a page on a test environment against the production version. This extension opens a new tab with the same page on prod in a single click.

<h2>Toggle Petrovich Device Type</h2>
We have a cookie that determines the user's device type and, accordingly, which version of the site is served — desktop or mobile. This extension toggles it to the opposite value and reloads the page in one click.