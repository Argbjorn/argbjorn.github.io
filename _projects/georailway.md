---
layout: page
title: Georgian Railway Map
description: Unofficial site about passenger railway in Georgia
img: assets/img/p1_preview.jpg
importance: 1
category: work
related_publications: false
---

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/p1_1.jpg" title="Georgian Railway Map" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

The site, <a href="https://georailway.com/">Georgian Railway Map</a>, like many pet projects, was born out of my own pain. I lived in Georgia for a while and enjoyed traveling between Tbilisi and Batumi by train. Every tourist knows about it: modern, comfortable, tickets easy to buy online. The same can't be said for trains on other routes. The official website only offered a confusing table with departure and arrival times at terminal stations, while more detailed schedules were sometimes posted at a ticket window in some station, and kind people would forward photos of them to each other in chats.

<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/p1_2.jpg" title="Old GR website schedule" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/p1_3.jpg" title="Schedule from a train station" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/p1_4.jpg" title="Handmade map from 2019" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    The state of schedule before 2024
</div>

And although the official website has since been updated and a schedule published, a mass of the original problems remains:
1. Without a map, it's hard to figure out where you can even go by train.
2. To find out where and when you can depart from Kutaisi Airport, for example, you have to go through the schedule of every single train.
3. International trains are missing, ticket information is buried, and there are countless other small issues.
My site solved all of these problems.

I'll only cover the current state of georailway, even though it's been a long journey: development started before AI became mainstream and isn't over yet.

<h2>Concept</h2>
During development I followed a few principles. First, the site should be as simple and fast as possible for the end user: no unnecessary scripts, effects, or parallax. Second, the site should be free for me to run.

<h2>Source data</h2>
Train data and schedules are the foundation. I store them in a Google Spreadsheets table. Why that instead of a real database? A few reasons.
1. Simplicity. When I learn about changes, I can update the information from my phone in a few clicks. Rolling back edits or granting access to AI is just as easy.
2. It's free. The terms of other services — such as those offering free tiers for cloud databases — keep changing. Google is far more stable and predictable in that regard.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/p1_5.jpg" title="Source data" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<h2>Keeping it up to date</h2>
A parser runs against the official site once a day and notifies me in Telegram if it finds any discrepancies with my data. Changes need to be verified manually, because sometimes valid trains disappear from the site, and sometimes the schedule is just wrong. Once I've checked, I send the parser's message to Claude and it updates the data in my schedule.
Interestingly, users sometimes reach out with fresh news that hasn't yet made it onto the official site.

<h2>Architecture</h2>
The site is built with Hugo — a static site generator. Typically, Hugo users just pick a theme and create pages as plain .md files, which are then compiled into HTML.
Of course, I don't describe each train or station page individually. For my use case, Hugo's Content Adapters feature is a perfect fit: it generates pages from a template based on data files. More on those in a moment.
The main page with the map is essentially a standalone project in vanilla JS. Building it is where I learned how maps work, what a state manager is, and much more. After numerous iterations, I ended up with a convenient, fast, mobile-friendly UX. The one and only up-to-date, interactive map of Georgian railways.

<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/p1_7.jpg" title="Route page" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/p1_8.jpg" title="Route on a map" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/p1_9.jpg" title="Main page source code" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<h2>Data files</h2>
I mentioned that pages are built from data files — these are essentially the site's backend. The format is plain JSON, but what's interesting is that they're assembled not just from my schedule data in Google Spreadsheets, but also from OpenStreetMap data. Station coordinates and names, the route geometry for the map, and the entire rail network all come from there.

<h2>Tests, build, and deployment</h2>
The site is hosted on GitHub Pages, so GitHub Actions handles the build and deployment.
Before the site itself is built, the data files are compiled, map routes are updated, the set of stations in a route is compared between OSM and my local data, and the data file tests are run.

<h2>UI tests</h2>
UI tests live in a <a href="https://github.com/Argbjorn/georgian-railway-frontend-tests">separate repository</a> and also run via GitHub Actions once a day.

<h2>Source code</h2>
The repository is open and available at <a href="https://github.com/Argbjorn/georgian-railway-frontend">GitHub</a>.

