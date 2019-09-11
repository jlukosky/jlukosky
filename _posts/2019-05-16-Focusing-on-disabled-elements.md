---
layout: post
title: "Focusing on disabled elements: should disabled form elements receive focus?"
date: 2019-05-18
author: "John Lukosky"
category: accessibility
description: "An analysis of whether disabled form elements should be a web page's focus order"
tags: [disabled,focus,forms,screen reader]
ogimage: "https://jlukosky.github.io/assets/2019/05/horsesblurred.jpg"
---

![A sharply focused horse on a beach next to two blurred horses](/assets/2019/05/horsesblurred.jpg)

A friend of mine insists that disabled form fields should be focusable. Their reasoning, as a blind person, is that it makes it easier to determine the contents of a form. We certainly don't want to hide anything.

Let's look at what makes a disabled form element special. According to [HTML5 4.13 Disabled elements](https://www.w3.org/TR/2014/REC-html5-20141028/disabled-elements.html) the following elements can be actually disabled using the disabled attribute:

- 'button'
- 'input'
- 'select'
- 'textarea'
- 'optgroup'
- 'option'
- 'fieldset'

When these elements are disabled they cannot be focused. They will also match the :disabled pseudo-class.

Did you notice the `a` element isn't in that list? If you're using anchors for buttons and other nonsense this is one more reason to reform your ways and follow semantics. Anchors don't support the disabled attribute.

Screen readers can still read these items but only through browsing the text with arrows. Even tabindex="0" is not going to work in this case.
As you can see from the allowed elements, disabled is only allowed on form controls. At times some may attempt to use it on the anchor element (a) but this will have no effect.

Another consideration for these disabled elements is they are no longer subject to WCAG contrast requirements. They could be impossible to read and still be compliant. This stacks up oddly against what is happening for non-visual users. Non-visual users can read the disabled element's properties but this is not necessarily true for sighted users, particularly those with low vision.

## The verdict - disabled shouldn't focus

In this battle it seems clear that disabled elements should not be focusable given that 

1. HTML5 says disabled elements don't belong in the focus order and
2. Screen readers don't override this behavior
3. Screen readers (and sharp-eyed sighted folks) can read the disabled element and
4. The disabled element isn't going to be submitted anyway.

## Other options to consider

So what to do with my friend who wants the disabled element to be more available? All is not lost, there are a couple of alternatives:

1. If it is an 'input' or 'textarea' element consider making it read-only instead of disabled.
2. If warranted, remove disabled elements instead of having them cluttering your form.
