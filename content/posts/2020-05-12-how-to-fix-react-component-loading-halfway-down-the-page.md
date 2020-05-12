---
template: post
title: How to fix react component loading halfway down the page
slug: react-component-loading-halfway
draft: false
priority: 10
date: 2020-05-12T02:16:01.115Z
description: fix react component loading halfway down the page on click
category: Web Development
tags:
  - react
  - how to fix page loading halfway in react
---
**S**o you're building a website with react and on a page you have a component which renders another page on click, but when you click and the page loads, it loads the page halfway. It is really annoying when the component page content is lengthy and your users would have to scroll back all the way to the top to view the content from the beginning. Well I've got good news for you, it can be fixed with some lines of code.

A quick fix would be to add the following lines of code on the component rendering it's page halfway.

```javascript
componentDidMount() {
    window.scrollTo(0, 0)
  }
```

If you are running react 16. and above, a more elegant and reusable fix would be to create a `<ScrollToTop/>` component which can be imported and used wherever you have such an issue. The content of the `<ScrollToTop/>` component would look like thus: 

```javascript
import { useEffect } from "react";
import { useLocation } from "react-router-dom";

export default function ScrollToTop() {
  const { pathname } = useLocation();

  useEffect(() => {
    window.scrollTo(0, 0);
  }, [pathname]);

  return null;
}
```