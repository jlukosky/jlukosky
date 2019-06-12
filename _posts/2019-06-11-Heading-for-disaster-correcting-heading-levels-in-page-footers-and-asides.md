---
layout: post
title: "Heading for disaster: correcting heading levels in page footers and asides"
date: 2019-06-11
author: "John Lukosky"
category: accessibility
description: "Correcting heading levels in page footers and asides"
tags: [[headings](../tags/index.md#headings),landmarks]
ogimage: "https://jlukosky.github.io/assets/2019/06/headings.jpg"
---

![A sharply focused horse on a beach next to two blurred horses](/assets/2019/06/headings.jpg)

It's commonly known that each page should have a single heading 1. This often restates the title of the web document. Each major heading section below should start with `<h2>`. There should never be a skip of level as in `<h1>` proceeding directly to `<h3>`.

A little less known is the top-level heading on independent sections of a web page (besides the main section) should begin with `<h2>`. This applies to sections such as footers and asides and probably to navigation sections that use headings.

- Aside (complementary landmark) since it is designed to make sense even when separated from the main content.
- Footer (contentinfo landmark) since it is designed to provide site-wide information that is not tied to the page's main content.

## Common issues

### Headings for footer or aside are child headings of main content

Often headings in a page's footer (or aside) are sequenced to come after the last heading in the main content. This doesn't make sense. The footer is a cross-site section that contains information that doesn't relate to a particular page's content. As an example, how can an `<h4>` in the main content that discusses snow shovels be the parent heading of the footer `<h5>` heading "Important resources"?

Why not reset all the way back to `<h1>`? The subject of the page trumps the other headings. It would be inappropriate to set the first heading in a footer or aside to the level of `<h1>`.

### Headings for footer or aside are arbitrarily set

Another method I've encountered is the "heck with it" method. Developers get frustrated getting bugs that their footer heading levels are not proper just settle on an arbitrary heading level. This is three levels of wrong:

1. Headings in the footer don't sequence after the main area and
2. Applying code without understanding what the effects are. Yes, even if a tester is shouting "this has to be fixed!".

## The alternative: reset the top heading of independent sections to level 2

The aside element implicitly has the complementary landmark role. Complementary landmarks should relate to the main content at a similar level in the DOM while remaining meaningful when separated from the main content. Clearly, headings in the aside (or complementary landmark) should begin with level 2.

The footer element implicitly has the contentinfo landmark role. Contentinfo landmarks identify common information at the bottom of each page within a website. This information typically includes copyright information and links to privacy and accessibility policies. The content applies site-wide, not to each page specifically. If headings are used in the footer  (or contentinfo landmark), begin these with level 2 as well.

To read more about proper heading structures, [W3C's Headings tutorial](https://www.w3.org/WAI/tutorials/page-structure/headings/#main-heading-before-navigation) is a great start.
