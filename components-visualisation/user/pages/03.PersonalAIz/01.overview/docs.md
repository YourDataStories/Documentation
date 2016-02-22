---
title: Overview
taxonomy:
    category: docs
---


**PersonalAIz** is a platform which contains useful modules to extend the functionality of **PServer**. The functionality of the compatible modules
varies from recommendation engines and data import endpoints to web components like Admin Panels, REST APIs and CMS plugins.

> **PersonalAIz Architecture:**

![PersonalAIz Architecture](/user/images/personalaiz.jpg)

**PServer** is an **application agnostic server** that supports user modeling in a variety of domains (e.g. marketplaces, news content websites,
music portals, etc.). It relies on a simple generic representation of the user model, using custom defined features per application. In more
detail, PServer supports modeling of users at different levels: personal models, stereotypes, communities, while adopting a unified approach
which hides the implementation details behind a simple and efficient API. Furthermore, it is capable of handling large volumes of data, as it
exploits state-of-the-art technologies such as MapReduce techniques and distributed storage systems.

> **PServer Architecture:**

![PServer Architecture](/user/images/pserver.jpg)