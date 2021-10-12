---
layout: post
title: (Primefaces) Spring 4 and JSF 2 without web.xml
---

It's not easy to use annotated Spring 4+ and Primefaces. There are some ways to use it with web.xml, but it can clash in some issues in resolving variables/properties with JSP sites.

This fix shows how to use both without any clashes and it's able to use JSF composites too, stored in folder "myProject/src/main/webapp/WEB-INF/resources/composites/myComponent.xhtml"

<script src="https://gist.github.com/anonymous/6501e9fb22dc357cd55c.js"></script>

<script src="https://gist.github.com/anonymous/fffb2ac14ecd90e758c5.js"></script>

<script src="https://gist.github.com/anonymous/3b069c4dd1b6c68fe7af.js"></script>