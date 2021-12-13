---
slug: thiet-lap-docusaurus
title: Cài đặt docusaurus
authors: [taitd]
tags: [docusaurus]
---

## Custom theme cho docusaurus

```css {12,15-18}
@import url("https://fonts.googleapis.com/css2?family=Inter:wght@100;200;300;400;500;600;700;800;900&display=swap");

:root {
  --ifm-color-primary: #25c2a0;
  --ifm-color-primary-dark: rgb(33, 175, 144);
  --ifm-color-primary-darker: rgb(31, 165, 136);
  --ifm-color-primary-darkest: rgb(26, 136, 112);
  --ifm-color-primary-light: rgb(70, 203, 174);
  --ifm-color-primary-lighter: rgb(102, 212, 189);
  --ifm-color-primary-lightest: rgb(146, 224, 208);
  --ifm-code-font-size: 95%;
  font-family: "Inter", sans-serif;
}

p {
  line-height: 28px;
}
```
